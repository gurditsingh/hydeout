# kafka Consumer
The primary role of a Kafka consumer is to take Kafka connection and consumer properties to read records from the appropriate Kafka topic. Complexities of concurrent application consumption, offset management, delivery semantics, and a lot more are taken care by Consumer APIs.

## Subscribing and Unsubscribing to Topics
Kafka use a `KafkaConsumer` to subscribe to Kafka topics and receive messages from these topics.

 -  The subscribe method. The method signature for subscribe takes in a collection of strings, which represent a list of topics.
 - A single consumer can subscribe to any number of topics from one to infinity.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjg0OTY3OTQ1LC0xODk1OTg5NTUxLDIxMT
c4MTI4ODEsMTUwNTI3MDI5NiwtMTk2ODY3MTczLC02MzczMzYw
MDYsLTgyMjgxODI0MCwtMjA3MzM1NDY3OCwxMjU3OTEzNzY4LC
03MzQyNjMxOTMsMTcxNzIxOTc3NCwtOTM5NzM2MTU4LC0xMDA5
NjQ1MDEzLC03OTIwOTg5MDIsLTE2MTY2Mjg4MTYsLTEwMjgwNj
I5MjUsMTgwMzM1NDUyNiwtNDI2NzU5NjgzLC0xMjU3MTAxMDM1
LDE2Mzg5MjM5MDNdfQ==
-->