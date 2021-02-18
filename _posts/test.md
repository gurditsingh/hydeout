## Join Operation on Streaming
Structured Streaming supports joining a streaming DataFrame with a static DataFrame as well as another streaming DataFrame. The result of the streaming join is generated incrementally, similar to the results of streaming aggregations.

## Joining Stream with Static data
In many of the cases, you won't be working with stream of data only. Only many a times you are required to join the screaming data with other data sets back to our scenario.

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
 - **Left Outer Join :** Left Outer join type is supported when streaming dataframe on left side of the join and it's not Stateful.
 - **Right Outer Join :** Right Outer join type is supported when streaming dataframe on right side of the join and it's not Stateful.
 - **Full Outer Join :** Full Outer join type is not Supported.



<!--stackedit_data:
eyJoaXN0b3J5IjpbMzQxOTE3MzQsNDA4MjAzNDg2LC0xOTQ4ND
UzOTY1LDY2MzUzNDg2OCwzNjA0ODA2ODAsMTAxODEwMDIxMywx
NTYyNzc1NTY3LDU0NTExNjMyMywxNjkzMzg5NjU5LC0zNTkxND
UzNTksNDc2NDM1MDQ3LC0xMTc1NTM2ODc5LDYyOTgwMjc3Myw2
MjQ2MjAyMTAsMTE5OTMxNDU2MiwtMTI5NTQwMTQ2OCw0MzI3Nj
k3NDcsNTUxMjQ2NjYsNDQ5NzQyOCw3OTk3MzkxNzJdfQ==
-->