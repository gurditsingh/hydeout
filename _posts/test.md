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

## why is this a Stateful operation?


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3Mjg4MzczMSwtNzQ1NTg0NzEzLC02ND
cyOTk2NzgsNDA4MjAzNDg2LC0xOTQ4NDUzOTY1LDY2MzUzNDg2
OCwzNjA0ODA2ODAsMTAxODEwMDIxMywxNTYyNzc1NTY3LDU0NT
ExNjMyMywxNjkzMzg5NjU5LC0zNTkxNDUzNTksNDc2NDM1MDQ3
LC0xMTc1NTM2ODc5LDYyOTgwMjc3Myw2MjQ2MjAyMTAsMTE5OT
MxNDU2MiwtMTI5NTQwMTQ2OCw0MzI3Njk3NDcsNTUxMjQ2NjZd
fQ==
-->