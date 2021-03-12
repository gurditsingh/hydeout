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
 
 
 Let's undstand by below example first we have **alice** as a record and we inserted to KStream like same for **marc** as well. last we have **alice** again we inserted into KStream.
 
   ![kstream](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/kstream.jpg?raw=true)
   
**Operators supported by KStream:**
`KStream` comes with a rich set of operators that allow for building topologies to consume, process and produce key-value records.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2ODk5MDg5NTIsNDgyNzYzMjAsMTE4MT
MxNjQxLC0xOTI3MjU3ODcwLDE2MTExMDQxMDUsLTExNDMxNzYw
NjYsMTc1MjMzMDk1NSwtMTM0ODQ4NDg0OSwtMTkyMjAxMDkxNC
w0OTA4NjA2NTYsNzYxOTM4MTcyLC02MjY0NjAwMDQsMTMwMTMy
MjQ0MiwtMTY5Mjc2NzcwLC04NTI4NjE3NDcsMTMyMjYyMTMzMC
wxMzYwNDM0MjUsMTAxNTgxMzUzNCwtMjA4ODc0NjYxMiwyMDU2
NzA2MTA1XX0=
-->