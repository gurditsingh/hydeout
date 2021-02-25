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
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbODI5ODAzNjA5LDYzOTUzNTAwMCwxNjM2OD
g5MDUyLC02NzYyMTM5NjYsLTEwODgyMTQ1NTQsLTExMTM1NjM4
MjYsLTE5NDQ2Nzc0NDAsMTY3Mjg4MzczMSwtNzQ1NTg0NzEzLC
02NDcyOTk2NzgsNDA4MjAzNDg2LC0xOTQ4NDUzOTY1LDY2MzUz
NDg2OCwzNjA0ODA2ODAsMTAxODEwMDIxMywxNTYyNzc1NTY3LD
U0NTExNjMyMywxNjkzMzg5NjU5LC0zNTkxNDUzNTksNDc2NDM1
MDQ3XX0=
-->