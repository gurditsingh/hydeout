# Kafka
Kafka is everywhere these days. With the advent of Microservices, Big Data and distributed computing. Kafka has become a regular occurrence in architecture’s of every product. This is all well and great, but stripped down to its core, Kafka is a distributed, horizontally scalable, fault-tolerant commit log.

## Lets proceed with Kafka storage internals:
You have some basic understanding about Kafka. With reference to storage in Kafka, you’ll always hear two terms, Partition and Topic.

 ## Kafka Topic
 Kafka Topic caters the entire purpose. Kafka topics are really just a named feed or category of messages. One way to think of it would be to consider a mailbox. It's an addressable, referenceable collection point for messages that producers send messages to and consumers retrieve messages from. **Topic is merely a logical grouping of several partitions.** 

In Kafka, a topic is a logical entity, something that virtually spans across the entire cluster of brokers. Producers and consumers alike don't really know or care about where and how the messages are kept. They just care about the topic to work with.

 - **Topic is from a logical viewpoint**
 
	 Topics can span an entire cluster of brokers for the benefit of scalability and fault tolerance.
	 
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbODM4ODA0NTg5LC0yMDU0NDg2NjgxLC00Nz
A0NTI2MDgsNjUwODk4MTgsLTIwODg3NDY2MTIsLTIwODg3NDY2
MTIsLTExNzE5Mjg0NSw5MzMzMDk3ODcsMTIxODQ3NjUwOSwtMT
czODQxNDAzLC04ODEwNDI1NjEsLTIwMTQzMjI4MzUsLTM3MzMy
NzU0NywyMzY5MTg0NDUsLTg1MTA4MDg1NSwtMTk3NTY4MTUzNC
wtMjAzNTgyMDM0NiwtNDUzODQ2MjY0LC0xODA4MzMxMTk0LDY1
OTI1Njk5Nl19
-->