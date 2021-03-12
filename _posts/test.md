## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using StreamsBuilder.stream) or as a result of transformations on an existing `KStream`.

```scala
val streamsBuilder: StreamsBuilder = new StreamsBuilder

streamsBuilder.stream[String,String]("input-topic")
```

 - Kstream is all inserts. Every data entered into kstream as insert new
   entry for each and every record stream.
   Ksream is similar to log just a ordered sequence of mags like a topic
   Kstream are infinite means unbounded data stream there is no end alwas
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkwNDYxNjA3MSwxMTgxMzE2NDEsLTE5Mj
cyNTc4NzAsMTYxMTEwNDEwNSwtMTE0MzE3NjA2NiwxNzUyMzMw
OTU1LC0xMzQ4NDg0ODQ5LC0xOTIyMDEwOTE0LDQ5MDg2MDY1Ni
w3NjE5MzgxNzIsLTYyNjQ2MDAwNCwxMzAxMzIyNDQyLC0xNjky
NzY3NzAsLTg1Mjg2MTc0NywxMzIyNjIxMzMwLDEzNjA0MzQyNS
wxMDE1ODEzNTM0LC0yMDg4NzQ2NjEyLDIwNTY3MDYxMDUsMTk2
NjgxMzU3OF19
-->