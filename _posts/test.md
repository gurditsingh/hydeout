
# Spark Structured Streaming Checkpointing

In Structured Streaming, if you enable checkpointing for a streaming query, then you can restart the query after a failure and the restarted query will continue where the failed one left off, while ensuring fault tolerance and data consistency guarantees.

## Why needed?
The primary goal of checkpointing is to ensure the fault-tolerance of streaming jobs. Thanks to the metadata stored in checkpoint files you will be able to restart your processing in case of any failure - business logic  or technical error.

Checkpoints are also important to guarantee at-least once processing in case of any failure in the middle of currently processed micro-batch.
<!--stackedit_data:
eyJoaXN0b3J5IjpbODg0MjY0NTI3LDE2NTYxMzI2MjgsMjQxNz
M4NDc3LDY4NDIwNTM3MCwxNjAwNDAzNDMxLC03MjcwMTUwMDcs
LTk1OTEzOTI3OCw5ODU2MzU2NTQsLTE1NDI2MDgyNTQsLTE5ND
IyODMyMjAsLTQyMjMxODk5NCwtMzI0MjgwNzMwLC0yMTE0NTAw
NDgzLC0yMTIyNDY1NzgxLDQ1ODg5MDAxMywtMTY1Njg3NzAxMC
wxMTgzNDUyMzQ4LC0xODk1OTg5NTUxLDIxMTc4MTI4ODEsMTUw
NTI3MDI5Nl19
-->