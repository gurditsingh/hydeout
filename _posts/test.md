
## How Transaction Log Works ?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the
log up to that point in Parquet format. 

Each log record object contains an array of actions. Whenever a user performs an action like INSERT, DELETE, UPDATE or MERGE the Delta Lake breaks that operation down into series of below steps :

 - **Update Metadata :** The metadata action changes the current metadata of the table. The metadata is a data structure containing the schema, partition column names and other configuration options, such as marking a table as append-only.
 - **Add File :** The add actions is used to add the file path into the log data structure. The add record for a data object can also include data statistics, such as the total record count and per-column min/max values and null counts.
 - **Remove File :** The remove actions is used to remove the file path from the log data structure. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzgzNjc0OSwxNzkwNjM1MDU1LDE0MDEzNj
g3NDMsLTE4NzA3MzU5OTMsLTE1NjQxNTg5NzgsMTkxMzQ0Nzcz
MCwxOTA2NDI5MzA2LC0yNjQ0NzY4MjAsMjcwODQwNjg2LC0yMD
U2NzQzMjc4LC0zMjE4NTc4NTksLTE1NDgxOTEwNDYsLTYwNjI2
Mzk5LDIxMTU0MzI3MzAsNjg1NjE1Mjk1LC03OTg1NDQ3MzgsMT
UwMjQyNzk2MywxNTMzODcxMjg5LDYxOTYxNDkyMyw3OTE2MzU3
NThdfQ==
-->