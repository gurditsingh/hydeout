
## What is Transaction Log or Delta Log?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing, zero-padded numerical IDs to store the log records
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQwMTM2ODc0MywtMTg3MDczNTk5MywtMT
U2NDE1ODk3OCwxOTEzNDQ3NzMwLDE5MDY0MjkzMDYsLTI2NDQ3
NjgyMCwyNzA4NDA2ODYsLTIwNTY3NDMyNzgsLTMyMTg1Nzg1OS
wtMTU0ODE5MTA0NiwtNjA2MjYzOTksMjExNTQzMjczMCw2ODU2
MTUyOTUsLTc5ODU0NDczOCwxNTAyNDI3OTYzLDE1MzM4NzEyOD
ksNjE5NjE0OTIzLDc5MTYzNTc1OCwtMTAyOTM2MjEzNywtMzU2
NjE5MjA4XX0=
-->