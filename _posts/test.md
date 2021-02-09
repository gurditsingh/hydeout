
# Spark Structured Streaming Checkpointing

In Structured Streaming, if you enable checkpointing for a streaming query, then you can restart the query after a failure and the restarted query will continue where the failed one left off, while ensuring fault tolerance and data consistency guarantees.

## Why needed?
The primary goal of checkpointing is to ensure the fault-tolerance of streaming jobs. Thanks to the metadata stored in checkpoint files you will be able to restart your processing in case of any failure - business logic or technical error.

Checkpoints are also important to guarantee at-least once processing in case of any failure in the middle of currently processed micro-batch.

## Enable checkpointing
To enable checkpointing, set the option `checkpointLocation` to a HDFS or cloud storage path. For example:
```scala
streamDataFrame.writeStream
  .format("csv")
  .option("path", "/outputStoragePath")
  .option("checkpointLocation", "/checkpointPath")
  .start()
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1NTUxMTc2NiwtMTY5MzEzODM1MSwxNj
U2MTMyNjI4LDI0MTczODQ3Nyw2ODQyMDUzNzAsMTYwMDQwMzQz
MSwtNzI3MDE1MDA3LC05NTkxMzkyNzgsOTg1NjM1NjU0LC0xNT
QyNjA4MjU0LC0xOTQyMjgzMjIwLC00MjIzMTg5OTQsLTMyNDI4
MDczMCwtMjExNDUwMDQ4MywtMjEyMjQ2NTc4MSw0NTg4OTAwMT
MsLTE2NTY4NzcwMTAsMTE4MzQ1MjM0OCwtMTg5NTk4OTU1MSwy
MTE3ODEyODgxXX0=
-->