
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
In Delta lake 
Think about the existence of the delta files for a second. The logs, versions, and files that are being generated must exist somewhere, some system or store for files. Log‐ Store is the general interface for all critical file system operations required to read and write the Delta transaction log. Because most storage systems do not provide atomic‐ ity guarantees out-of-the-box, Delta Lake transactional operations go through the LogStore API instead of accessing the storage system directly.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzUxMzM5NzYyLC05Mzg1MTA2MDAsMTM2Mj
M1ODExMiw1MjUyMDExNzcsMTIyODI3OTY0MiwxNzkwNjM1MDU1
LDE0MDEzNjg3NDMsLTE4NzA3MzU5OTMsLTE1NjQxNTg5NzgsMT
kxMzQ0NzczMCwxOTA2NDI5MzA2LC0yNjQ0NzY4MjAsMjcwODQw
Njg2LC0yMDU2NzQzMjc4LC0zMjE4NTc4NTksLTE1NDgxOTEwND
YsLTYwNjI2Mzk5LDIxMTU0MzI3MzAsNjg1NjE1Mjk1LC03OTg1
NDQ3MzhdfQ==
-->