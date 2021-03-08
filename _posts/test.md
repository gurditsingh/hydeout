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

## what is state in kafka streams:

Kafka Streams provides  **state stores**, which can be used by stream processing applications to store and query data, which is an important capability when implementing stateful operations. Kafka Streams automatically creates and manages such state stores when you are calling stateful operators such as  `count()`  or  `aggregate()`.

Every stream task in a Kafka Streams application may embed one or more local state stores that can be accessed via APIs to store and query data required for processing. These state stores can either be a  RocksDB  database, an in-memory hash map, or another convenient data structure. Kafka Streams offers fault-tolerance and automatic recovery for local state stores.

![window events](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/kafka-state-store.jpg?raw=true)

**Types of state:**

 - **Local or internal state :** State that is accessible only by a specific instance of streaming application. This state is usually maintained and managed with an embedded, in-memory database running within the application. The advantage of local state is that it is extremely fast. The disadvantage is that you are limited to the amount of memory available.
 
 - **External state :** State that is maintained in an external datastore, like NoSQL system or RDBMS. The advantages of an external state are its virtually unlimited size and the fact that it can be accessed from multiple instances of the application or even from different applications.

 
 

## Stream-Processing Design Patterns

 - **Single-Event Processing :** The most basic pattern of stream processing is the processing of each event one by one. This is also known as a map/filter pattern because it is commonly used to filter unnecessary events from the stream or transform each event. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MjcxOTgxOTEsLTYwOTA3NDI1OCw3OT
c4ODg1MTUsOTM5NDkxNTkzLC02Mjk2MDgyMTUsMTcxMzcxNDA0
NCwxNjcxMDAxMzQyLDEzMTk5MzI1MDUsMTE5NjI4MzMxNiwxNj
c4NTg1MTk1LC01MDEwMTMyNjEsMjAzNjc3MjQ0MywtMjA4ODc0
NjYxMiwtOTUwMDI1MDEyLC01MDQyNzM0NzAsLTExNjE3NDA1Nz
UsLTIxNDY1MTAwMDMsMjA4MjYwMTYxNiwtMjExMzcyOTkzMiwt
OTMxNjIxOTVdfQ==
-->