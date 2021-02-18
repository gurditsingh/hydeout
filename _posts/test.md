## Join Operation on Streaming
Structured Streaming supports joining a streaming DataFrame with a static DataFrame as well as another streaming DataFrame. The result of the streaming join is generated incrementally, similar to the results of streaming aggregations.

## Joining Stream with Static data
In many of the cases, you won't be working with stream of data only. Only many a times you are required to join the Streaming data with other static data sets.

```scala
val streamingDF = spark.readStream
      .format("kafka")
      .option("kafka.bootstrap.servers", "localhost:9092")
      .option("subscribe", "join_events")
      .load()

val staticDF=spark.read
      .option("header","true")
      .option("inferSchema","true")
      .csv("input_path")
      
val joinDF = streamingDF.join(staticDF,List("id"),"inner")
```
Note that **stream-static joins are not stateful**, so no state management is necessary.

### Supported Join Types

 - **Inner Join :**  Inner join type is Supported and it's not not Stateful
 - **Left Outer Join :** Left Outer join type is supported when streaming DataFrame on left side of the join and it's not Stateful.
 - **Right Outer Join :** Right Outer join type is supported when streaming DataFrame on right side of the join and it's not Stateful.
 - **Full Outer Join :** Full Outer join type is not Supported.

-----
## Joining Stream with Stream
Spark added support for stream-stream joins, that is, you can join two streaming DataFrames. In which we can join multiple streams together.

```scala
val streamingDFTest1 = spark.readStream
      .format("kafka")
      .option("kafka.bootstrap.servers", "localhost:9092")
      .option("subscribe", "join_events_test1")
      .load()

val streamingDFTest2 = spark.readStream
      .format("kafka")
      .option("kafka.bootstrap.servers", "localhost:9092")
      .option("subscribe", "join_events_test2")
      .load()
      
val joinDF = streamingDFTest1.join(streamingDFTest2,List("id"),"inner")
```
Note that **stream-stream joins are stateful**, so state management is necessary.

 The challenge of generating join results between two data streams is that, at any point of time,
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzM4OTAwMDYsLTY0NzI5OTY3OCw0MDgyMD
M0ODYsLTE5NDg0NTM5NjUsNjYzNTM0ODY4LDM2MDQ4MDY4MCwx
MDE4MTAwMjEzLDE1NjI3NzU1NjcsNTQ1MTE2MzIzLDE2OTMzOD
k2NTksLTM1OTE0NTM1OSw0NzY0MzUwNDcsLTExNzU1MzY4Nzks
NjI5ODAyNzczLDYyNDYyMDIxMCwxMTk5MzE0NTYyLC0xMjk1ND
AxNDY4LDQzMjc2OTc0Nyw1NTEyNDY2Niw0NDk3NDI4XX0=
-->