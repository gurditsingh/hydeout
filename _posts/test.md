## Streams Architecture

Kafka Streams simplifies application development by building on the Apache Kafka producer and consumer APIs, and leveraging the native capabilities of Kafka to offer data parallelism, distributed coordination, fault tolerance, and operational simplicity.

 - Kafka Streams is a client library for stream processing applications that process records in kafka topics.
 - Kafka streams provides the high level DSL like KStream and KTable.
 - Kafka streams provide the wrapper around the kafka Producer and Consumer API's.
 - Kafka streams provide the Topology to describe the flow of the stream.
 - In Kafka streams the Topology process one record at a time.
 - Kafka streams application can be run in multiple instances. 

## Core Concepts:

 

 - **Stream :** Stream is a sequence of immutable data records that are fully oredered 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA3NjE3Njk3OSwtMTA4ODIxNDU1NCwtMT
ExMzU2MzgyNiwtMTk0NDY3NzQ0MCwxNjcyODgzNzMxLC03NDU1
ODQ3MTMsLTY0NzI5OTY3OCw0MDgyMDM0ODYsLTE5NDg0NTM5Nj
UsNjYzNTM0ODY4LDM2MDQ4MDY4MCwxMDE4MTAwMjEzLDE1NjI3
NzU1NjcsNTQ1MTE2MzIzLDE2OTMzODk2NTksLTM1OTE0NTM1OS
w0NzY0MzUwNDcsLTExNzU1MzY4NzksNjI5ODAyNzczLDYyNDYy
MDIxMF19
-->