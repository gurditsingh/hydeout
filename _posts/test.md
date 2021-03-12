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
`KStream` comes with a rich set of operators that allow for building topologies to consume, process and produce key-value records. below are the few operators. Check out the rich set of [operators](https://jaceklaskowski.gitbooks.io/mastering-kafka-streams/content/kafka-streams-KStream.html#contract).

| Operator  | Description  |
| ------------ | ------------ |
| Branch  |  Branch (or split) a KStream based on the supplied predicates into one or more KStream instances.  |
| Filter  | Evaluates a boolean function for each element and retains those for which the function returns true.  |
| FlatMap  | Takes one record and produces zero, one, or more records. You can modify the record keys and values, including their types.  |
| FlatMapValues   |  Takes one record and produces zero, one, or more records, while retaining the key of the original record. You can modify the record values and the value type. |
| Map  | Takes one record and produces one record. You can modify the record key and value, including their types.  |
| MapValues  | Takes one record and produces one record, while retaining the key of the original record. You can modify the record value and the value type.  |
| GroupByKey  |  Groups the records by the existing key. |
| GroupBy  |  Groups the records by a new key, which may be of a different key type. When grouping a table, you may also specify a new value and value type. |
|   |   |


## What is KTable
`KTable` is the abstraction of a **changelog stream** from a primary-keyed table. Each record in the changelog stream is an update on the primary-keyed table with the record key as the primary key.

`KTable` assumes that records from the source topic that have `null` keys are simply dropped.

`KTable` can be created directly from a Kafka topic (using [StreamsBuilder.table](https://jaceklaskowski.gitbooks.io/mastering-kafka-streams/content/kafka-streams-StreamsBuilder.html#table) operator), as a result of [transformations](https://jaceklaskowski.gitbooks.io/mastering-kafka-streams/content/kafka-streams-KTable.html#operators) on an existing `KTable`, or aggregations (`aggregate`, `count`, and `reduce`)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU3NzAzMDQxNSwtMTY4OTkwODk1Miw0OD
I3NjMyMCwxMTgxMzE2NDEsLTE5MjcyNTc4NzAsMTYxMTEwNDEw
NSwtMTE0MzE3NjA2NiwxNzUyMzMwOTU1LC0xMzQ4NDg0ODQ5LC
0xOTIyMDEwOTE0LDQ5MDg2MDY1Niw3NjE5MzgxNzIsLTYyNjQ2
MDAwNCwxMzAxMzIyNDQyLC0xNjkyNzY3NzAsLTg1Mjg2MTc0Ny
wxMzIyNjIxMzMwLDEzNjA0MzQyNSwxMDE1ODEzNTM0LC0yMDg4
NzQ2NjEyXX0=
-->