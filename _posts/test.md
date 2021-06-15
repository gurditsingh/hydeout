
## What is Transaction Log or Delta Log?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the
log up to that point in Parquet format. 

Each log record object contains an array of actions:

 - Update metadata

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODI3NjI0OTYsMTQwMTM2ODc0MywtMT
g3MDczNTk5MywtMTU2NDE1ODk3OCwxOTEzNDQ3NzMwLDE5MDY0
MjkzMDYsLTI2NDQ3NjgyMCwyNzA4NDA2ODYsLTIwNTY3NDMyNz
gsLTMyMTg1Nzg1OSwtMTU0ODE5MTA0NiwtNjA2MjYzOTksMjEx
NTQzMjczMCw2ODU2MTUyOTUsLTc5ODU0NDczOCwxNTAyNDI3OT
YzLDE1MzM4NzEyODksNjE5NjE0OTIzLDc5MTYzNTc1OCwtMTAy
OTM2MjEzN119
-->