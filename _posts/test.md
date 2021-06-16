
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

	**Let's read the first transaction log of version and see the schema **
	```scala
	spark.read.json("delta_load_table/_delta_log/00000000000000000000.json").printSchema()
	```

## LogStore Implementation
In Delta lake generate the transaction log files and they must exist somewhere like some storage systems to store the files. Delta Lake ACID guarantees the atomicity and durability of the storage system. Delta lake relies on the following when interacting with storage systems.

 - **Atomic visibility :** Any file written through this store must be made visible, atomically means be visible entirely or not visible at all.
 - **Mutual exclusion :** Only one writer must be able to create a file at the final destination.
 - **Consistent listing :** Once a file has been written in a directory, it should offers ACID consistent listing of files.

Because storage systems do not necessarily provide all of these guarantees out-of-the-box. For that Delta Lake used the Log store API to provide the ACID guarantees for different storage systems, user can use different `LogStore` implementations.

[LogStore API code](https://github.com/delta-io/delta/blob/b76e2314583b0e2081a01163cea628031384b987/core/src/main/scala/io/delta/storage/LogStore.java#L69 "LogStore API code")

The `LogStore`, similar to Apache Spark, uses Hadoop FileSystem API to perform reads and writes. So Delta Lake supports concurrent reads on any storage system that provides an implementation of FileSystem API.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg3MDA3MDA4MSwtMTMwNTUyMzU2NywtMT
Q1OTkyNzU3NSwtOTM4NTEwNjAwLDEzNjIzNTgxMTIsNTI1MjAx
MTc3LDEyMjgyNzk2NDIsMTc5MDYzNTA1NSwxNDAxMzY4NzQzLC
0xODcwNzM1OTkzLC0xNTY0MTU4OTc4LDE5MTM0NDc3MzAsMTkw
NjQyOTMwNiwtMjY0NDc2ODIwLDI3MDg0MDY4NiwtMjA1Njc0Mz
I3OCwtMzIxODU3ODU5LC0xNTQ4MTkxMDQ2LC02MDYyNjM5OSwy
MTE1NDMyNzMwXX0=
-->