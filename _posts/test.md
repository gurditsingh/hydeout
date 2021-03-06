## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. **Repartitioning Topic :-**
 
	 In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are **Map, FlatMap and SelectKey** etc. Repartitioning is done automatically take care by kafka streams behind the scenes.


	**Can we avoid the repartition or why do we need repartition ?**
	In kafka stream architecture when we changed the key data needs to be shuffle/repartitioned around the streaming application where data need to written back to kafka and again reads the data back from the new key and grouped the data.
	
	
 2. **Changelog Topic :-**
 
	 In case of your streaming application if you start aggregation then kafka stream save aggregated data into changelog topic which is created by kafka streams internally.
 
	 Actually the result of aggregation call creates a state store and for fault-tolerance the state store is backed up by a Kafka Changelog topic. The aggregation results are stored into this internal topic. State will be recovered from changelog topic when applications is restarted and application-id wasn't changed.

	

> Kafka Streams allows for stateful stream processing, i.e. operators that have an internal state. This internal state is managed in so-called state stores. A state store can be ephemeral (lost on failure) or fault-tolerant (restored after the failure). The default implementation used by Kafka Streams DSL is a fault-tolerant state store using 1. an internally created and compacted changelog topic (for fault-tolerance) and 2. one (or multiple) RocksDB instances (for  cached key-value lookups). Thus, in case of starting/stopping  applications and rewinding/reprocessing, this internal data needs to get managed correctly.


## Lets see in sample example

In the below example we changed the key by **selectKey**() operator and also apply the aggregation by **groupByKey**(). After running the job kafka internally creates **Repartitioning Topic** and **Changelog Topic**
```scala
Properties config = new Properties();  
config.put(StreamsConfig.APPLICATION_ID_CONFIG, "Test");  
config.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");  
config.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG, Serdes.String().getClass());  
config.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG, Serdes.String().getClass());  
  
StreamsBuilder streamsBuilder = new StreamsBuilder();  
  
KStream<String, String> inputStream = streamsBuilder.stream("in_word");  
  
inputStream.mapValues(value -> value.toLowerCase())  
        .flatMapValues(value -> Arrays.asList(value.split("#")))  
        .selectKey((key, value) -> value)  
        .groupByKey()  
        .count()  
        .toStream()  
        .to("out_word");  
  
  
KafkaStreams ks = new KafkaStreams(streamsBuilder.build(), config);  
ks.start();

``` 
If we list all the topic in kafka then we can see internal topics are created. because kafka stream internally use consumer API that's way _offsets topic is created.
 
```shell
Test-KSTREAM-AGGREGATE-STATE-STORE-0000000004-changelog
Test-KSTREAM-AGGREGATE-STATE-STORE-0000000004-repartition
__consumer_offsets
in_word
out_word
```

## what is State in kafka streams:
In general Stream processing becomes really interesting when you have operations that involve multiple events: counting the number of events by type, moving averages, joining two streams, etc. In those cases, you need to keep track of more information— how many events of each type did we see this hour, all events that require joining, sums, averages, etc. We call the information that is stored between events a state.

It is often to store the state in variables that are local to the stream processing application logic, such as a simple hash-table to store moving counts. However, this is not a reliable approach for managing state in stream processing because when the stream-processing application is stopped, the state is lost, which changes the results. This is usually not the desired outcome, so care should be taken to persist the most recent state and recover it when starting the application.

**Types of state:**

 - **Local or internal state**

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4MjU0MDE1NiwxMzE5OTMyNTA1LDExOT
YyODMzMTYsMTY3ODU4NTE5NSwtNTAxMDEzMjYxLDIwMzY3NzI0
NDMsLTIwODg3NDY2MTIsLTk1MDAyNTAxMiwtNTA0MjczNDcwLC
0xMTYxNzQwNTc1LC0yMTQ2NTEwMDAzLDIwODI2MDE2MTYsLTIx
MTM3Mjk5MzIsLTkzMTYyMTk1LDYzOTUzNTAwMCwxNjM2ODg5MD
UyLC02NzYyMTM5NjYsLTEwODgyMTQ1NTQsLTExMTM1NjM4MjYs
LTE5NDQ2Nzc0NDBdfQ==
-->