
## How Transaction Log Works ?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the
log up to that point in Parquet format. 

Each log record object contains an array of actions. Whenever a user performs an action like INSERT, DELETE, UPDATE or MERGE the Delta Lake breaks that operation down into series of below steps :

 - **Update Metadata :** The metadata action changes the current metadata of the table. The metadata is a data structure containing the schema, partition column names and other configuration options, such as marking a table as append-only.
 - **Add File :** The add actions is used to add the file path into the log data structure. The add record for a data object can also include data statistics, such as the total record count and per-column min/max values and null counts.
 - **Remove File :** The remove actions is used to remove the file path from the log data structure. The remove action includes a timestamp that indicates when the removal occurred. Physical deletion of the data object can happen lazily after a user-specified retention time threshold.
 - **Set transaction :** To record own data inside log records, which can be useful for implementing end-to-end transactional application like structured streaming job has committed a micro-batch with the given ID and store appId and version fields in txn action.
 - Change protocol

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzQ1NTkwNzg4LDEyMjgyNzk2NDIsMTc5MD
YzNTA1NSwxNDAxMzY4NzQzLC0xODcwNzM1OTkzLC0xNTY0MTU4
OTc4LDE5MTM0NDc3MzAsMTkwNjQyOTMwNiwtMjY0NDc2ODIwLD
I3MDg0MDY4NiwtMjA1Njc0MzI3OCwtMzIxODU3ODU5LC0xNTQ4
MTkxMDQ2LC02MDYyNjM5OSwyMTE1NDMyNzMwLDY4NTYxNTI5NS
wtNzk4NTQ0NzM4LDE1MDI0Mjc5NjMsMTUzMzg3MTI4OSw2MTk2
MTQ5MjNdfQ==
-->