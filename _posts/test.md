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

## Kafka Partitions

The topic, as a logical concept, is represented by one or more physical log files called partitions. **Partitions** are the units of storage in Kafka for messages.

The number of partitions per topic is entirely configurable. The partition itself is central to how Apache Kafka achieves **scalability**, greater levels of **fault tolerance** and higher levels of **throughput**.

Each topic has to have a single partition because that partition, as I mentioned, is the physical representation of the topic as a commit log stored on one or more brokers. The log maintained on the broker's file system in the directory tmp/kafka‑logs. For the topic subfolder created called my_topic‑0, which contained the log for that single partition.

**Partition As a memory standpoint**


 
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTExNjQzMSwtOTY5OTU5MzYsLTE2Nj
A1NDkzNjksLTE2MzQ3NTM3MTUsMTE4NTU3NzA3MCwtMjA1NDQ4
NjY4MSwtNDcwNDUyNjA4LDY1MDg5ODE4LC0yMDg4NzQ2NjEyLC
0yMDg4NzQ2NjEyLC0xMTcxOTI4NDUsOTMzMzA5Nzg3LDEyMTg0
NzY1MDksLTE3Mzg0MTQwMywtODgxMDQyNTYxLC0yMDE0MzIyOD
M1LC0zNzMzMjc1NDcsMjM2OTE4NDQ1LC04NTEwODA4NTUsLTE5
NzU2ODE1MzRdfQ==
-->