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
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDg0NTM5NjUsNjYzNTM0ODY4LDM2MD
Q4MDY4MCwxMDE4MTAwMjEzLDE1NjI3NzU1NjcsNTQ1MTE2MzIz
LDE2OTMzODk2NTksLTM1OTE0NTM1OSw0NzY0MzUwNDcsLTExNz
U1MzY4NzksNjI5ODAyNzczLDYyNDYyMDIxMCwxMTk5MzE0NTYy
LC0xMjk1NDAxNDY4LDQzMjc2OTc0Nyw1NTEyNDY2Niw0NDk3ND
I4LDc5OTczOTE3MiwtMjM0Mzg5NDAsLTIwODI5NTMyNDBdfQ==

-->