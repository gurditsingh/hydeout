
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

	**Sample Log file :**
	```json
	{"commitInfo":{"timestamp":1623662581422,"userId":"4377377090523225","userName":"gurdit.singh","operation":"CREATE TABLE AS SELECT","operationParameters":{"isManaged":"false","description":null,"partitionBy":"[]","properties":"{}"},"notebook":{"notebookId":"2238652198370632"},"clusterId":"0614-080750-tipi733","isolationLevel":"WriteSerializable","isBlindAppend":true}}
	{"protocol":{"minReaderVersion":1,"minWriterVersion":2}}
	{"metaData":{"id":"f63544f8-4e82-451b-ad40-1345322ed8ab","format":{"provider":"parquet","options":{}},"schemaString":"{\"type\":\"struct\",\"fields\":[{\"name\":\"addr_state\",\"type\":\"string\",\"nullable\":true,\"metadata\":{}},{\"name\":\"sum\",\"type\":\"integer\",\"nullable\":true,\"metadata\":{}}]}","partitionColumns":[],"configuration":{},"createdTime":1623662574380}}
	{"add":{"path":"part-00000-0e287e04-fc6d-43c0-8415-a2341a543f8f-c000.snappy.parquet","partitionValues":{},"size":873,"modificationTime":1623662581000,"dataChange":true,"stats":"{\"numRecords\":52,\"minValues\":{\"addr_state\":\"AK\",\"sum\":1},\"maxValues\":{\"addr_state\":\"WY\",\"sum\":1},\"nullCount\":{\"addr_state\":1,\"sum\":0}}"}}
	```

## LogStore Implementation
In Delta lake generate the transaction log files and they must exist somewhere like some storage systems to store the files. Delta Lake ACID guarantees the atomicity and durability of the storage system. Delta lake relies on the following when interacting with storage systems.

 - **Atomic visibility :** Any file written through this store must be made visible, atomically means be visible entirely or not visible at all.
 - **Mutual exclusion :** Only one writer must be able to create a file at the final destination.
 - **Consistent listing :** 

Because storage systems do not necessarily provide the guarantees of ACID, Atomic visibility, out-of-the-box

Think about the existence of the delta files for a second. The logs, versions, and files that are being generated must exist somewhere, some system or store for files. Log‐ Store is the general interface for all critical file system operations required to read and write the Delta transaction log. Because most storage systems do not provide atomic‐ ity guarantees out-of-the-box, Delta Lake transactional operations go through the LogStore API instead of accessing the storage system directly.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzNTA0MTksLTE0NTk5Mjc1NzUsLTkzOD
UxMDYwMCwxMzYyMzU4MTEyLDUyNTIwMTE3NywxMjI4Mjc5NjQy
LDE3OTA2MzUwNTUsMTQwMTM2ODc0MywtMTg3MDczNTk5MywtMT
U2NDE1ODk3OCwxOTEzNDQ3NzMwLDE5MDY0MjkzMDYsLTI2NDQ3
NjgyMCwyNzA4NDA2ODYsLTIwNTY3NDMyNzgsLTMyMTg1Nzg1OS
wtMTU0ODE5MTA0NiwtNjA2MjYzOTksMjExNTQzMjczMCw2ODU2
MTUyOTVdfQ==
-->