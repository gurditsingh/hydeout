# Kafka
Kafka is everywhere these days. With the advent of Microservices, Big Data and distributed computing. Kafka has become a regular occurrence in architecture’s of every product. This is all well and great, but stripped down to its core, Kafka is a distributed, horizontally scalable, fault-tolerant commit log.

## Lets proceed with Kafka storage internals:
You have some basic understanding about Kafka. With reference to storage in Kafka, you’ll always hear two terms, Partition and Topic.

 ## Kafka Topic
 Kafka Topic caters the entire purpose. Kafka topics are really just a named feed or category of messages. One way to think of it would be to consider a mailbox. It's an addressable, referenceable collection point for messages that producers send messages to and consumers retrieve messages from. **Topic is merely a logical grouping of several partitions.** 

In Kafka, a topic is a logical entity, something that virtually spans across the entire cluster of brokers. Producers and consumers alike don't really know or care about where and how the messages are kept. They just care about the topic to work with.


<!--stackedit_data:
eyJoaXN0b3J5IjpbODUyMzY5NjgsLTIwNTQ0ODY2ODEsLTQ3MD
Q1MjYwOCw2NTA4OTgxOCwtMjA4ODc0NjYxMiwtMjA4ODc0NjYx
MiwtMTE3MTkyODQ1LDkzMzMwOTc4NywxMjE4NDc2NTA5LC0xNz
M4NDE0MDMsLTg4MTA0MjU2MSwtMjAxNDMyMjgzNSwtMzczMzI3
NTQ3LDIzNjkxODQ0NSwtODUxMDgwODU1LC0xOTc1NjgxNTM0LC
0yMDM1ODIwMzQ2LC00NTM4NDYyNjQsLTE4MDgzMzExOTQsNjU5
MjU2OTk2XX0=
-->