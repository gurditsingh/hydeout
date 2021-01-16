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
 - **key and value serializers**

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxODUyOTkzNyw2MTEwMDkzNjMsMTE2OD
Q5ODIwMiw3NTIyNDk3MTUsLTI4ODQwNjQ4NywxNjE3NDk1NzQ0
LDM2MjYxOTQ4MSwxNjI0MzQzMDQwLDIwMzU4MjE1MzQsLTEyOT
gxMTIzMTQsLTQ0NTIzMDczMCwtOTY5OTU5MzYsLTE2NjA1NDkz
NjksLTE2MzQ3NTM3MTUsMTE4NTU3NzA3MCwtMjA1NDQ4NjY4MS
wtNDcwNDUyNjA4LDY1MDg5ODE4LC0yMDg4NzQ2NjEyLC0yMDg4
NzQ2NjEyXX0=
-->