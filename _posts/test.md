
## What is Transaction Log or Delta Log?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the
table. It contains a sequence of JSON objects with increasing,
zero-padded numerical IDs to store the log records
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MTgzNDIyMDksLTE4NzA3MzU5OTMsLT
E1NjQxNTg5NzgsMTkxMzQ0NzczMCwxOTA2NDI5MzA2LC0yNjQ0
NzY4MjAsMjcwODQwNjg2LC0yMDU2NzQzMjc4LC0zMjE4NTc4NT
ksLTE1NDgxOTEwNDYsLTYwNjI2Mzk5LDIxMTU0MzI3MzAsNjg1
NjE1Mjk1LC03OTg1NDQ3MzgsMTUwMjQyNzk2MywxNTMzODcxMj
g5LDYxOTYxNDkyMyw3OTE2MzU3NTgsLTEwMjkzNjIxMzcsLTM1
NjYxOTIwOF19
-->