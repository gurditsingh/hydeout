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
Note that stream-static joins are not stateful, so no state management is necessary.

### Supported Join Types

 - **Inner Join :**  Inner join type is Supported and it's not not Stateful
 - **Left Outer Join :** Left Outer join type is supported when streaming DataFrame on left side of the join and it's not Stateful.
 - **Right Outer Join :** Right Outer join type is supported when streaming DataFrame on right side of the join and it's not Stateful.
 - **Full Outer Join :** Full Outer join type is not Supported.

-----
## Joining Stream with Stream
Spark added support for stream-stream joins, that is, you can join two streaming DataFrames. In which we can join multiple streams together.

```scala
val streamingDF = spark.readStream
      .format("kafka")
      .option("kafka.bootstrap.servers", "localhost:9092")
      .option("subscribe", "join_events")
      .load()

val streamingDF = spark.readStream
      .format("kafka")
      .option("kafka.bootstrap.servers", "localhost:9092")
      .option("subscribe", "join_events")
      .load()
      
val joinDF = streamingDF.join(staticDF,List("id"),"inner")
```

 The challenge of generating join results between two data streams is that, at any point of time,
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI1OTUwMTU0OSwtNjQ3Mjk5Njc4LDQwOD
IwMzQ4NiwtMTk0ODQ1Mzk2NSw2NjM1MzQ4NjgsMzYwNDgwNjgw
LDEwMTgxMDAyMTMsMTU2Mjc3NTU2Nyw1NDUxMTYzMjMsMTY5Mz
M4OTY1OSwtMzU5MTQ1MzU5LDQ3NjQzNTA0NywtMTE3NTUzNjg3
OSw2Mjk4MDI3NzMsNjI0NjIwMjEwLDExOTkzMTQ1NjIsLTEyOT
U0MDE0NjgsNDMyNzY5NzQ3LDU1MTI0NjY2LDQ0OTc0MjhdfQ==

-->