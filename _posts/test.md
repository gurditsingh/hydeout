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
Like in kafka consumer and producer application we set some config parameters same way we need to pass to streaming application. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjgwMDMxMjI5LDIwODI2MDE2MTYsLTIxMT
M3Mjk5MzIsLTkzMTYyMTk1LDYzOTUzNTAwMCwxNjM2ODg5MDUy
LC02NzYyMTM5NjYsLTEwODgyMTQ1NTQsLTExMTM1NjM4MjYsLT
E5NDQ2Nzc0NDAsMTY3Mjg4MzczMSwtNzQ1NTg0NzEzLC02NDcy
OTk2NzgsNDA4MjAzNDg2LC0xOTQ4NDUzOTY1LDY2MzUzNDg2OC
wzNjA0ODA2ODAsMTAxODEwMDIxMywxNTYyNzc1NTY3LDU0NTEx
NjMyM119
-->