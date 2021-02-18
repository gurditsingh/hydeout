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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY1NDMwMDY4LDQwODIwMzQ4NiwtMTk0OD
Q1Mzk2NSw2NjM1MzQ4NjgsMzYwNDgwNjgwLDEwMTgxMDAyMTMs
MTU2Mjc3NTU2Nyw1NDUxMTYzMjMsMTY5MzM4OTY1OSwtMzU5MT
Q1MzU5LDQ3NjQzNTA0NywtMTE3NTUzNjg3OSw2Mjk4MDI3NzMs
NjI0NjIwMjEwLDExOTkzMTQ1NjIsLTEyOTU0MDE0NjgsNDMyNz
Y5NzQ3LDU1MTI0NjY2LDQ0OTc0MjgsNzk5NzM5MTcyXX0=
-->