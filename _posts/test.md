## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using StreamsBuilder.stream) or as a result of transformations on an existing `KStream`.

```scala
val streamsBuilder: StreamsBuilder = new StreamsBuilder

streamsBuilder.stream[String,String]("input-topic")
```

Kstream is all inserts. Every data entenered into kstream as insert new e

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTE1MzA5Mzc2LDExODEzMTY0MSwtMTkyNz
I1Nzg3MCwxNjExMTA0MTA1LC0xMTQzMTc2MDY2LDE3NTIzMzA5
NTUsLTEzNDg0ODQ4NDksLTE5MjIwMTA5MTQsNDkwODYwNjU2LD
c2MTkzODE3MiwtNjI2NDYwMDA0LDEzMDEzMjI0NDIsLTE2OTI3
Njc3MCwtODUyODYxNzQ3LDEzMjI2MjEzMzAsMTM2MDQzNDI1LD
EwMTU4MTM1MzQsMjA1NjcwNjEwNSwxOTY2ODEzNTc4LC02MDkw
NzQyNThdfQ==
-->