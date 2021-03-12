## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using [StreamsBuilder.stream](https://jaceklaskowski.gitbooks.io/mastering-kafka-streams/content/kafka-streams-StreamsBuilder.html#stream) operator) or as a result of [transformations](https://jaceklaskowski.gitbooks.io/mastering-kafka-streams/content/kafka-streams-KStream.html#operators) on an existing `KStream`.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNzE0NTI3NSwtMTkyNzI1Nzg3MCwxNj
ExMTA0MTA1LC0xMTQzMTc2MDY2LDE3NTIzMzA5NTUsLTEzNDg0
ODQ4NDksLTE5MjIwMTA5MTQsNDkwODYwNjU2LDc2MTkzODE3Mi
wtNjI2NDYwMDA0LDEzMDEzMjI0NDIsLTE2OTI3Njc3MCwtODUy
ODYxNzQ3LDEzMjI2MjEzMzAsMTM2MDQzNDI1LDEwMTU4MTM1Mz
QsLTIwODg3NDY2MTIsMjA1NjcwNjEwNSwxOTY2ODEzNTc4LC02
MDkwNzQyNThdfQ==
-->