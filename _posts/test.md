# kafka Consumer
The primary role of a Kafka consumer is to take Kafka connection and consumer properties to read records from the appropriate Kafka topic. Complexities of concurrent application consumption, offset management, delivery semantics, and a lot more are taken care by Consumer APIs.

## Subscribing and Unsubscribing to Topics
Kafka use a `KafkaConsumer` to subscribe to Kafka topics and receive messages from these topics.

 -  The subscribe method. The method signature for subscribe takes in a collection of strings, which represent a list of topics.
 - A single consumer can subscribe to any number of topics from one to infinity.
 - User can subscribe by passing a regular expression as the parameter, which is a useful overload for the subscribe method.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4MzQ1MjM0OCwtMTg5NTk4OTU1MSwyMT
E3ODEyODgxLDE1MDUyNzAyOTYsLTE5Njg2NzE3MywtNjM3MzM2
MDA2LC04MjI4MTgyNDAsLTIwNzMzNTQ2NzgsMTI1NzkxMzc2OC
wtNzM0MjYzMTkzLDE3MTcyMTk3NzQsLTkzOTczNjE1OCwtMTAw
OTY0NTAxMywtNzkyMDk4OTAyLC0xNjE2NjI4ODE2LC0xMDI4MD
YyOTI1LDE4MDMzNTQ1MjYsLTQyNjc1OTY4MywtMTI1NzEwMTAz
NSwxNjM4OTIzOTAzXX0=
-->