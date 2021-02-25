## Streams Architecture

Kafka Streams simplifies application development by building on the Apache Kafka producer and consumer APIs, and leveraging the native capabilities of Kafka to offer data parallelism, distributed coordination, fault tolerance, and operational simplicity.

 - Kafka Streams is a client library for stream processing applications that process records in kafka topics.
 - Kafka streams provides the high level DSL like KStream and KTable.
 - Kafka streams provide the wrapper around the kafka Producer and Consumer API's.
 - Kafka streams provide the Topology to describe the flow of the stream.
 - In Kafka streams the Topology process one record at a time.
 - Kafka streams application can be run in multiple instances. 

## Core Concepts:

 
![window events](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/kafka-topology.png?raw=true) 
 - **Stream :** A Stream is a sequence of immutable data records that are fully ordered, can be restart and fault tolerant.
 - **Stream Processor :** A Stream Processor defines the stream processing computational logic for your application, means how input data is transformed into output data. Stream Processor is a node in a processor topology/graph. It process record by record and create new stream after each stream processor. There are two special processors in the topology:
	-   **Source Processor**: A source processor is a special type of  stream processor that does not have any upstream processors. It produces an input stream to its topology from one or multiple Kafka topics by consuming records from these topics and forward them to its down-stream processors.
	-   **Sink Processor**: A sink processor is a special type of stream processor that does not have down-stream processors. It sends any received records from its up-stream processors to a specified Kafka topic.
- **Topology :** A Topology is a graph of processors chained together by streams.


## Kafka Stream API's at developer side

### Topology

 - It represents the streaming processing logic of kafka stream application.
 - It is a DAG (directed acyclic graph) of processors.
 - By Topology API developer can add sources , processors and sinks.
 - Developer can describe the topology and see the logical representation.
 
 
 **Example:**
```scala
val streamsBuilder = new StreamsBuilder
val topology = streamsBuilder.build()
println(topology.describe())
``` 

### Kafka Streams

 - It manages execution of topology of kafka stream application like start, close and state
 - It consumes records from and produce results to kafka topic.
 - To create multiple kafka streams instances per kafka stream application.
 
 **Example:**
 ```scala
val config = ....
val streamsBuilder = ....
....
....
val kafkaStreams = new KafkaStreams(streamsBuilder.build(),config)
kafkaStreams.start()
```

## Configuration parameter for Streaming application
Like in kafka consumer and producer application we set some config parameters same way we need to pass to streaming application. In kafka streams application we can apply bunch of parameters but lets describe the requires one.

 1. **application . id**  Each stream processing application must have a unique ID. The same ID must be given to all instances of the application. This ID is used in the couple of other places to isolate resources used by the application from others.
	 -   As the default Kafka consumer and producer  `client.id`  prefix
	-   As the Kafka consumer  `group.id`  for coordination
	-   As the name of the subdirectory in the state directory (`state.dir`)
	-   As the prefix of internal Kafka topic names
	
2. **bootstrap . servers** This is the same setting that is used by the underlying producer and consumer clients to connect to the Kafka cluster.

**Example:**
```scala
val config=new Properties();
config.put(StreamsConfig.APPLICATION_ID_CONFIG,"app_id")
config.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG,"localhost:9092")
config.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG,Serdes.String().getClass)
config.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG,Serdes.String().getClass)
```

## Let's Build first word count application with kafka stream
lets describe the Topology of different processors to perform word count example

 1. Read data from kafka topic and define the **Source Processor**.
 2. Next define the **MapValues processor** to transform the values to lowercase.
 3. Next define the **FlatMapValues processor** to split the one incoming record into number of outgoing records.
 4. Next define the **SelectKey processor** to apply the value of the record as key.
 5. Next define the **GroupByKey processor** to aggregate the data on key.
 6. Next define the **Count processor** to count the result on aggregated data.
 7. Next define the **Sink processor** the write the data to kafka topic.

**Example:**
```scala
val config = new Properties()
config.put(StreamsConfig.APPLICATION_ID_CONFIG, "app_id")
config.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092")
config.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG, Serdes.String().getClass)
config.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG, Serdes.String().getClass)

    val streamsBuilder: StreamsBuilder = new StreamsBuilder


    streamsBuilder.stream("input_data")
      .mapValues((value: String) => value.toLowerCase)
      .flatMapValues((value: String) => util.Arrays.asList(value.split("|")))
      .selectKey((key: String, value: String) => value)
      .groupByKey
      .count
      .toStream.to("output_data")


    val kafkaStreams = new KafkaStreams(streamsBuilder.build(), config)
    kafkaStreams.start()
```

## Describe the Topology and Shutdown the application
**Describe the Topology** or logging the topology is helpful in development and it's helpful to understand the application flow. The topology represents all the sources,  processors and sinks of your application.
 **Example:**
 ```scala
val config = ....
val streamsBuilder = ....
....
....
val kafkaStreams = new KafkaStreams(streamsBuilder.build(),config)
kafkaStreams.start()

```

**Shutdown the application** is good for any application. To 



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUyMDgxMjkyLC0xMTYxNzQwNTc1LC0yMT
Q2NTEwMDAzLDIwODI2MDE2MTYsLTIxMTM3Mjk5MzIsLTkzMTYy
MTk1LDYzOTUzNTAwMCwxNjM2ODg5MDUyLC02NzYyMTM5NjYsLT
EwODgyMTQ1NTQsLTExMTM1NjM4MjYsLTE5NDQ2Nzc0NDAsMTY3
Mjg4MzczMSwtNzQ1NTg0NzEzLC02NDcyOTk2NzgsNDA4MjAzND
g2LC0xOTQ4NDUzOTY1LDY2MzUzNDg2OCwzNjA0ODA2ODAsMTAx
ODEwMDIxM119
-->