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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNTQzMTU1OSw0MDgyMDM0ODYsLTE5ND
g0NTM5NjUsNjYzNTM0ODY4LDM2MDQ4MDY4MCwxMDE4MTAwMjEz
LDE1NjI3NzU1NjcsNTQ1MTE2MzIzLDE2OTMzODk2NTksLTM1OT
E0NTM1OSw0NzY0MzUwNDcsLTExNzU1MzY4NzksNjI5ODAyNzcz
LDYyNDYyMDIxMCwxMTk5MzE0NTYyLC0xMjk1NDAxNDY4LDQzMj
c2OTc0Nyw1NTEyNDY2Niw0NDk3NDI4LDc5OTczOTE3Ml19
-->