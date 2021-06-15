
## How Transaction Log Works ?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the
log up to that point in Parquet format. 

Each log record object contains an array of actions. Whenever a user performs an action like INSERT, DELETE, UPDATE or MERGE the Delta Lake breaks that operation down into series of below steps :

 - **Update metadata :** The metadata action changes the current metadata of the table. The metadata is a data structure containing the schema, partition column names and other configuration options, such as marking a table as append-only.
 - **Add file :** The add actions is used to add the file path into the log data structure. The add record for a data object can also include data statistics, such as the total record count and per-column min/max values and null counts.
 - **Remove file :** The remove actions is used to remove the file path from the log data structure. The remove action includes a timestamp that indicates when the removal occurred. Physical deletion of the data object can happen lazily after a user-specified retention time threshold.
 - **Set transaction :** To record own data inside log records, which can be useful for implementing end-to-end transactional application like structured streaming job has committed a micro-batch with the given ID and store appId and version fields in txn action.
 - **Change protocol :** The protocol action is used to increase the version of the Delta protocol that is required to read or write a given table.
 - **Commit info :** The commit info data structure contains the information of user commit means which operation was made, where, what time and etc.



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM2MjM1ODExMiw1MjUyMDExNzcsMTIyOD
I3OTY0MiwxNzkwNjM1MDU1LDE0MDEzNjg3NDMsLTE4NzA3MzU5
OTMsLTE1NjQxNTg5NzgsMTkxMzQ0NzczMCwxOTA2NDI5MzA2LC
0yNjQ0NzY4MjAsMjcwODQwNjg2LC0yMDU2NzQzMjc4LC0zMjE4
NTc4NTksLTE1NDgxOTEwNDYsLTYwNjI2Mzk5LDIxMTU0MzI3Mz
AsNjg1NjE1Mjk1LC03OTg1NDQ3MzgsMTUwMjQyNzk2MywxNTMz
ODcxMjg5XX0=
-->