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

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDA4MjAzNDg2LC0xOTQ4NDUzOTY1LDY2Mz
UzNDg2OCwzNjA0ODA2ODAsMTAxODEwMDIxMywxNTYyNzc1NTY3
LDU0NTExNjMyMywxNjkzMzg5NjU5LC0zNTkxNDUzNTksNDc2ND
M1MDQ3LC0xMTc1NTM2ODc5LDYyOTgwMjc3Myw2MjQ2MjAyMTAs
MTE5OTMxNDU2MiwtMTI5NTQwMTQ2OCw0MzI3Njk3NDcsNTUxMj
Q2NjYsNDQ5NzQyOCw3OTk3MzkxNzIsLTIzNDM4OTQwXX0=
-->