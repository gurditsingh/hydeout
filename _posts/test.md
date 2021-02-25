## Streams Architecture

Kafka Streams simplifies application development by building on the Apache Kafka producer and consumer APIs, and leveraging the native capabilities of Kafka to offer data parallelism, distributed coordination, fault tolerance, and operational simplicity.

 - Kafka Streams is a client library for stream processing applications that process records in kafka topics.
 - Kafka streams provides the high level DSL like KStream and KTable.
 - Kafka streams provide the wrapper around the kafka Producer and Consumer API's.
 - Kafka streams provide the Topology to describe the flow of the stream.
 - In Kafka streams the Topology process one record at a time.
 - Kafka streams application can be run in multiple instances. 

## Core Concepts:

 

 - **Stream :** A Stream is a sequence of immutable data records that are fully ordered, can be restart and fault tolerant.
 - **Stream Processor :** A Stream Processor defines the stream processing computational logic for your application, means how input data is transformed into output data. Stream Processor is a node in a processor topology/graph. It process record by record and create new stream after each stream processor. There are two special processors in the topology:
	-   **Source Processor**: A source processor is a special type of  stream processor that does not have any upstream processors. It produces an input stream to its topology from one or multiple Kafka topics by consuming records from these topics and forward them to its down-stream processors.
	-   **Sink Processor**: A sink processor is a special type of stream processor that does not have down-stream processors. It sends any received records from its up-stream processors to a specified Kafka topic.
- **Topology :** A Topology is a graph of processors chained together by streams.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYzNjg4OTA1MiwtNjc2MjEzOTY2LC0xMD
g4MjE0NTU0LC0xMTEzNTYzODI2LC0xOTQ0Njc3NDQwLDE2NzI4
ODM3MzEsLTc0NTU4NDcxMywtNjQ3Mjk5Njc4LDQwODIwMzQ4Ni
wtMTk0ODQ1Mzk2NSw2NjM1MzQ4NjgsMzYwNDgwNjgwLDEwMTgx
MDAyMTMsMTU2Mjc3NTU2Nyw1NDUxMTYzMjMsMTY5MzM4OTY1OS
wtMzU5MTQ1MzU5LDQ3NjQzNTA0NywtMTE3NTUzNjg3OSw2Mjk4
MDI3NzNdfQ==
-->