# kafka producer
Kafka Producer API allows applications to send streams of data to topics in the Kafka cluster. Basically Its a component of the Kafka ecosystem which is used to publish messages onto a Kafka topic.

# Kafka producer configurations
Having knowledge of producer configurations becomes critical for us in order to get optimal performance and to leverage the capabilities of Kafka. Let's look at each of them in detail below:

### - Configuration Properties : 
When creating a Kafka producer client application, first need an object to represent the required configuration properties needed to start up a producer. There are three required properties, bootstrap.servers and both key and value serializers.

Configuration items are generally key‑value pairs, the easiest way to do it is to use the Properties class from the core java.util's library.

<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ0MTMyODQ5LDYxMTAwOTM2MywxMTY4ND
k4MjAyLDc1MjI0OTcxNSwtMjg4NDA2NDg3LDE2MTc0OTU3NDQs
MzYyNjE5NDgxLDIwMzU4MjE1MzQsLTEyOTgxMTIzMTQsLTQ0NT
IzMDczMCwtOTY5OTU5MzYsLTE2NjA1NDkzNjksLTE2MzQ3NTM3
MTUsMTE4NTU3NzA3MCwtMjA1NDQ4NjY4MSwtNDcwNDUyNjA4LD
Y1MDg5ODE4LC0yMDg4NzQ2NjEyLC0yMDg4NzQ2NjEyLC0xMTcx
OTI4NDVdfQ==
-->