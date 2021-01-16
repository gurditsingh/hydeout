# kafka producer
Kafka Producer API allows applications to send streams of data to topics in the Kafka cluster. Basically Its a component of the Kafka ecosystem which is used to publish messages onto a Kafka topic.

# Kafka producer configurations
Having knowledge of producer configurations becomes critical for us in order to get optimal performance and to leverage the capabilities of Kafka. Let's look at each of them in detail below:

### - Configuration Properties : 
When creating a Kafka producer client application, first need an object to represent the required configuration properties needed to start up a producer. There are three required properties, bootstrap.servers and both key and value serializers.

Configuration items are generally key‑value pairs, the easiest way to do it is to use the Properties class from the core java.util's library.

 - **bootstrap.servers :** 
	 - The bootstrap.servers configuration setting needed for the producer to start up and supply a list of brokers (best practice to provide more than one broker).
	 - The producer doesn't connect to every broker referenced in this list, just the first available one.
	 - The broker it connects to for discovering the full membership of the cluster.
	 - The membership  determine the partition owners or leaders so that when it's ready to send messages.
	 
 - **Key and Value serializers :**
	 - key and value serializers are basically to encode the message content.
	 - This is to optimize the size of the messages not only for network transmission, but for storage and even compression.
	 - the producer that serves as the beginning of a message's lifecycle, it is responsible for describing how the message contents are to be encoded so the consumer can know how to decode them.
 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNzg1ODM0NDgsNjExMDA5MzYzLDExNj
g0OTgyMDIsNzUyMjQ5NzE1LC0yODg0MDY0ODcsMTYxNzQ5NTc0
NCwzNjI2MTk0ODEsMTYyNDM0MzA0MCwyMDM1ODIxNTM0LC0xMj
k4MTEyMzE0LC00NDUyMzA3MzAsLTk2OTk1OTM2LC0xNjYwNTQ5
MzY5LC0xNjM0NzUzNzE1LDExODU1NzcwNzAsLTIwNTQ0ODY2OD
EsLTQ3MDQ1MjYwOCw2NTA4OTgxOCwtMjA4ODc0NjYxMiwtMjA4
ODc0NjYxMl19
-->