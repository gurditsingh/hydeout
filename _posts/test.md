
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
 - **Commit info :** The commit info data strucContains information around the commit, which operation was made, from where, and at what time.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NzYxMzgxMTgsNTI1MjAxMTc3LDEyMj
gyNzk2NDIsMTc5MDYzNTA1NSwxNDAxMzY4NzQzLC0xODcwNzM1
OTkzLC0xNTY0MTU4OTc4LDE5MTM0NDc3MzAsMTkwNjQyOTMwNi
wtMjY0NDc2ODIwLDI3MDg0MDY4NiwtMjA1Njc0MzI3OCwtMzIx
ODU3ODU5LC0xNTQ4MTkxMDQ2LC02MDYyNjM5OSwyMTE1NDMyNz
MwLDY4NTYxNTI5NSwtNzk4NTQ0NzM4LDE1MDI0Mjc5NjMsMTUz
Mzg3MTI4OV19
-->