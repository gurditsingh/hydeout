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
   

	 
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTY0NTI4NDksLTIwNTQ0ODY2ODEsLT
Q3MDQ1MjYwOCw2NTA4OTgxOCwtMjA4ODc0NjYxMiwtMjA4ODc0
NjYxMiwtMTE3MTkyODQ1LDkzMzMwOTc4NywxMjE4NDc2NTA5LC
0xNzM4NDE0MDMsLTg4MTA0MjU2MSwtMjAxNDMyMjgzNSwtMzcz
MzI3NTQ3LDIzNjkxODQ0NSwtODUxMDgwODU1LC0xOTc1NjgxNT
M0LC0yMDM1ODIwMzQ2LC00NTM4NDYyNjQsLTE4MDgzMzExOTQs
NjU5MjU2OTk2XX0=
-->