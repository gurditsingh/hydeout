# kafka producer
Kafka Producer API allows applications to send streams of data to topics in the Kafka cluster. Basically Its a component of the Kafka ecosystem which is used to publish messages onto a Kafka topic.

# Kafka producer configurations
Having knowledge of producer configurations becomes critical for us in order to get optimal performance and to leverage the capabilities of Kafka. Let's look at each of them in detail below:

### - Configuration Properties : 
When creating a Kafka producer client application, first need an object to represent the required configuration properties needed to start up a producer. There are three required properties, bootstrap.servers and both key and value serializers.

Configuration items are generally key‑value pairs, the easiest way to do it is to use the Properties class from the core java.util's library.

 - **bootstrap.servers :** 
	 - The bootstrap.servers configuration setting needed for the producer to start up and supply a list of brokers.
	 - The producer doesn't connect to every broker referenced in this list, just the first available one.
	 - The broker it connects to for discovering the full membership of the cluster.
	 - The membership  determine the partition owners or leaders so that when it's ready to send messages

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY4NDUzMjc0MSw2MTEwMDkzNjMsMTE2OD
Q5ODIwMiw3NTIyNDk3MTUsLTI4ODQwNjQ4NywxNjE3NDk1NzQ0
LDM2MjYxOTQ4MSwyMDM1ODIxNTM0LC0xMjk4MTEyMzE0LC00ND
UyMzA3MzAsLTk2OTk1OTM2LC0xNjYwNTQ5MzY5LC0xNjM0NzUz
NzE1LDExODU1NzcwNzAsLTIwNTQ0ODY2ODEsLTQ3MDQ1MjYwOC
w2NTA4OTgxOCwtMjA4ODc0NjYxMiwtMjA4ODc0NjYxMiwtMTE3
MTkyODQ1XX0=
-->