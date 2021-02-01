# kafka Consumer
The primary role of a Kafka consumer is to take Kafka connection and consumer properties to read records from the appropriate Kafka topic. Complexities of concurrent application consumption, offset management, delivery semantics, and a lot more are taken care by Consumer APIs.

## Subscribing and Unsubscribing to Topics
Kafka use a `KafkaConsumer` to subscribe to Kafka topics and receive messages from these topics.

 -  The subscribe method. The method signature for subscribe takes in a collection of strings, which represent a list of topics.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzOTc3OTg2NTUsMjExNzgxMjg4MSwxNT
A1MjcwMjk2LC0xOTY4NjcxNzMsLTYzNzMzNjAwNiwtODIyODE4
MjQwLC0yMDczMzU0Njc4LDEyNTc5MTM3NjgsLTczNDI2MzE5My
wxNzE3MjE5Nzc0LC05Mzk3MzYxNTgsLTEwMDk2NDUwMTMsLTc5
MjA5ODkwMiwtMTYxNjYyODgxNiwtMTAyODA2MjkyNSwxODAzMz
U0NTI2LC00MjY3NTk2ODMsLTEyNTcxMDEwMzUsMTYzODkyMzkw
MywtMTU4OTc4NjUxOF19
-->