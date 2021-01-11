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

The topic, as a logical concept, is represented by one or more physical log files called partitions. **_Partitions_** are the units of storage in Kafka for messages

 
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM1MzI2MzkxNywtMTY2MDU0OTM2OSwtMT
YzNDc1MzcxNSwxMTg1NTc3MDcwLC0yMDU0NDg2NjgxLC00NzA0
NTI2MDgsNjUwODk4MTgsLTIwODg3NDY2MTIsLTIwODg3NDY2MT
IsLTExNzE5Mjg0NSw5MzMzMDk3ODcsMTIxODQ3NjUwOSwtMTcz
ODQxNDAzLC04ODEwNDI1NjEsLTIwMTQzMjI4MzUsLTM3MzMyNz
U0NywyMzY5MTg0NDUsLTg1MTA4MDg1NSwtMTk3NTY4MTUzNCwt
MjAzNTgyMDM0Nl19
-->