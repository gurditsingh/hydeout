## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using StreamsBuilder.stream) or as a result of transformations on an existing `KStream`.

```scala
val streamsBuilder: StreamsBuilder = new StreamsBuilder

streamsBuilder.stream[String,String]("input-topic")
```

 - Kstream is all inserts. Every data entered into Kstream as insert new
   entry for each and every record stream.
 - Kstream is similar to log just a ordered sequence of mags like a
   topic.
 - Kstream are infinite means unbounded data stream there is no end always expects more data to come.
 
 
 Let's undstand by below example first we have alice as a record and we added to KStream 
   ![kstream](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/kstream.jpg?raw=true)
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5NDU0NzE1Niw0ODI3NjMyMCwxMTgxMz
E2NDEsLTE5MjcyNTc4NzAsMTYxMTEwNDEwNSwtMTE0MzE3NjA2
NiwxNzUyMzMwOTU1LC0xMzQ4NDg0ODQ5LC0xOTIyMDEwOTE0LD
Q5MDg2MDY1Niw3NjE5MzgxNzIsLTYyNjQ2MDAwNCwxMzAxMzIy
NDQyLC0xNjkyNzY3NzAsLTg1Mjg2MTc0NywxMzIyNjIxMzMwLD
EzNjA0MzQyNSwxMDE1ODEzNTM0LC0yMDg4NzQ2NjEyLDIwNTY3
MDYxMDVdfQ==
-->