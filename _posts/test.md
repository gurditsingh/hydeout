## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using StreamsBuilder.stream) or as a result of transformations on an existing `KStream`.

```scala
val streamsBuilder: StreamsBuilder = new StreamsBuilder

streamsBuilder.stream[String,String]("input-topic")
```

 - Kstream is all inserts. Every data entered into kstream as insert new
   entry for each and every record stream.
   Ksream is similar to log just a ordered sequence of mags

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5OTU2MDM5NDksMTE4MTMxNjQxLC0xOT
I3MjU3ODcwLDE2MTExMDQxMDUsLTExNDMxNzYwNjYsMTc1MjMz
MDk1NSwtMTM0ODQ4NDg0OSwtMTkyMjAxMDkxNCw0OTA4NjA2NT
YsNzYxOTM4MTcyLC02MjY0NjAwMDQsMTMwMTMyMjQ0MiwtMTY5
Mjc2NzcwLC04NTI4NjE3NDcsMTMyMjYyMTMzMCwxMzYwNDM0Mj
UsMTAxNTgxMzUzNCwyMDU2NzA2MTA1LDE5NjY4MTM1NzgsLTYw
OTA3NDI1OF19
-->