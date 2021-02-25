## Streams Architecture

Kafka Streams simplifies application development by building on the Apache Kafka producer and consumer APIs, and leveraging the native capabilities of Kafka to offer data parallelism, distributed coordination, fault tolerance, and operational simplicity.

 - Kafka Streams is a client library for stream processing applications that process records in kafka topics.
 - Kafka streams provides the high level DSL like KStream and KTable.
 - Kafka streams provide the wrapper around the kafka Producer and Consumer API's.
 - Kafka streams provide the Topology to describe the flow of the stream.
 - In Kafka streams the Topology process one record at a time.
 - Kafka streams application can be run in multiple instances. 

## Core Concepts:

 

 - **Stream :** Stream is a sequence of immutable data records that are fully ordered, can be restart and fault tolerant.
 - Stream Processor

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAzNjg4NTIwOSwtNjc2MjEzOTY2LC0xMD
g4MjE0NTU0LC0xMTEzNTYzODI2LC0xOTQ0Njc3NDQwLDE2NzI4
ODM3MzEsLTc0NTU4NDcxMywtNjQ3Mjk5Njc4LDQwODIwMzQ4Ni
wtMTk0ODQ1Mzk2NSw2NjM1MzQ4NjgsMzYwNDgwNjgwLDEwMTgx
MDAyMTMsMTU2Mjc3NTU2Nyw1NDUxMTYzMjMsMTY5MzM4OTY1OS
wtMzU5MTQ1MzU5LDQ3NjQzNTA0NywtMTE3NTUzNjg3OSw2Mjk4
MDI3NzNdfQ==
-->