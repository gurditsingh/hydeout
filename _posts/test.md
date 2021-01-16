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
	 - It uses the broker it connects to for discovering the full membership of the cluster, which, of course, can change at any time.

<!--stackedit_data:
eyJoaXN0b3J5IjpbODE0Nzc3MzM0LDYxMTAwOTM2MywxMTY4ND
k4MjAyLDc1MjI0OTcxNSwtMjg4NDA2NDg3LDE2MTc0OTU3NDQs
MzYyNjE5NDgxLDE2MjQzNDMwNDAsMjAzNTgyMTUzNCwtMTI5OD
ExMjMxNCwtNDQ1MjMwNzMwLC05Njk5NTkzNiwtMTY2MDU0OTM2
OSwtMTYzNDc1MzcxNSwxMTg1NTc3MDcwLC0yMDU0NDg2NjgxLC
00NzA0NTI2MDgsNjUwODk4MTgsLTIwODg3NDY2MTIsLTIwODg3
NDY2MTJdfQ==
-->