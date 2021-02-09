
# Spark Structured Streaming Checkpointing

In Structured Streaming, if you enable checkpointing for a streaming query, then you can restart the query after a failure and the restarted query will continue where the failed one left off, while ensuring fault tolerance and data consistency guarantees.

## Why needed?
The primary goal of checkpointing is to ensure the fault-tolerance of streaming jobs. Thanks to the metadata stored in checkpoint files you will be able to restart your processing in case of any failure - business logic or technical error.

Checkpoints are also important to guarantee at-least once processing in case of any failure in the middle of currently processed micro-batch.

## Enable checkpointing
To enable checkpointing, set the option `checkpointLocation` to a HDFS or cloud storage path. For example:

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTMxMzgzNTEsMTY1NjEzMjYyOCwyND
E3Mzg0NzcsNjg0MjA1MzcwLDE2MDA0MDM0MzEsLTcyNzAxNTAw
NywtOTU5MTM5Mjc4LDk4NTYzNTY1NCwtMTU0MjYwODI1NCwtMT
k0MjI4MzIyMCwtNDIyMzE4OTk0LC0zMjQyODA3MzAsLTIxMTQ1
MDA0ODMsLTIxMjI0NjU3ODEsNDU4ODkwMDEzLC0xNjU2ODc3MD
EwLDExODM0NTIzNDgsLTE4OTU5ODk1NTEsMjExNzgxMjg4MSwx
NTA1MjcwMjk2XX0=
-->