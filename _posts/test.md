# Kafka
Kafka is everywhere these days. With the advent of Microservices, Big Data and distributed computing. Kafka has become a regular occurrence in architecture’s of every product. This is all well and great, but stripped down to its core, Kafka is a distributed, horizontally scalable, fault-tolerant commit log.

## Lets proceed with Kafka storage internals:
You have some basic understanding about Kafka. With reference to storage in Kafka, you’ll always hear two terms, Partition and Topic.

 ## Kafka Topic
 Kafka Topic caters the entire purpose. Kafka topics are really just a named feed or category of messages. One way to think of it would be to consider a mailbox. It's an addressable, referenceable collection point for messages that producers send messages to and consumers retrieve messages from. 

> Topic is merely a logical grouping of several partitions.

In Kafka, a topic is a logical entity, something that virtually spans across the entire cluster of brokers. Producers and consumers alike don't really know or care about where and how the messages are kept. They just care about the topic to work with.

 **Topic is from a logical viewpoint**

 - Topics can span an entire cluster of brokers for the benefit of
   scalability and fault tolerance.
 - With the abstraction of a topic, a producer simply needs to publish
   messages to that topic.
 - Similarly, consumers simply want to consume from a topic, regardless
   of where it is.

**What's happening within any given topic**

 - When a producer sends a message to a Kafka topic, the messages are appended to a time‑ordered sequential stream.
 - Each message represents an event, or fact, that from the perspective of the producer and make available to potential consumers.
 - These events are immutable. Once they are received into a topic, they cannot be changed.



 
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NjA1NDkzNjksLTE2MzQ3NTM3MTUsMT
E4NTU3NzA3MCwtMjA1NDQ4NjY4MSwtNDcwNDUyNjA4LDY1MDg5
ODE4LC0yMDg4NzQ2NjEyLC0yMDg4NzQ2NjEyLC0xMTcxOTI4ND
UsOTMzMzA5Nzg3LDEyMTg0NzY1MDksLTE3Mzg0MTQwMywtODgx
MDQyNTYxLC0yMDE0MzIyODM1LC0zNzMzMjc1NDcsMjM2OTE4ND
Q1LC04NTEwODA4NTUsLTE5NzU2ODE1MzQsLTIwMzU4MjAzNDYs
LTQ1Mzg0NjI2NF19
-->