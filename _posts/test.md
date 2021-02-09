
# Spark Structured Streaming Checkpointing

A production-grade streaming application must have robust failure handling. In Structured Streaming, if you enable checkpointing for a streaming query, then you can restart the query after a failure and the restarted query will continue where the failed one left off, while ensuring fault tolerance and data consistency guarantees. Hence, to make your queries fault tolerant, you must enable query checkpointing and configure Databricks [jobs](https://docs.databricks.com/jobs.html) to restart your queries automatically after a failure.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY1NjEzMjYyOCwyNDE3Mzg0NzcsNjg0Mj
A1MzcwLDE2MDA0MDM0MzEsLTcyNzAxNTAwNywtOTU5MTM5Mjc4
LDk4NTYzNTY1NCwtMTU0MjYwODI1NCwtMTk0MjI4MzIyMCwtND
IyMzE4OTk0LC0zMjQyODA3MzAsLTIxMTQ1MDA0ODMsLTIxMjI0
NjU3ODEsNDU4ODkwMDEzLC0xNjU2ODc3MDEwLDExODM0NTIzND
gsLTE4OTU5ODk1NTEsMjExNzgxMjg4MSwxNTA1MjcwMjk2LC0x
OTY4NjcxNzNdfQ==
-->