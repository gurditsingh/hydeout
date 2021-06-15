
## How Transaction Log Works ?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the
log up to that point in Parquet format. 

Each log record object contains an array of actions:

 - Update metadata

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIzMDgxODMxNSwxNDAxMzY4NzQzLC0xOD
cwNzM1OTkzLC0xNTY0MTU4OTc4LDE5MTM0NDc3MzAsMTkwNjQy
OTMwNiwtMjY0NDc2ODIwLDI3MDg0MDY4NiwtMjA1Njc0MzI3OC
wtMzIxODU3ODU5LC0xNTQ4MTkxMDQ2LC02MDYyNjM5OSwyMTE1
NDMyNzMwLDY4NTYxNTI5NSwtNzk4NTQ0NzM4LDE1MDI0Mjc5Nj
MsMTUzMzg3MTI4OSw2MTk2MTQ5MjMsNzkxNjM1NzU4LC0xMDI5
MzYyMTM3XX0=
-->