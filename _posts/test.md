## How Transaction Log Works ?

A Delta Lake table is a directory on file system that holds data files with the table contents and a log of transaction operations. The Delta Lake’s approach is to store a transaction log and metadata directly on file system no need to maintain separate service for metadata and log handling.

The transaction log is stored in the _delta_log subdirectory within the table. It contains a sequence of JSON objects with increasing numerical IDs. It also contain occasional checkpoints for specific log objects that summarize the log up to that point in Parquet format. 

### LogStore Implementation
In Delta lake generate the transaction log files and they must exist somewhere like some storage systems to store the files. Delta Lake ACID guarantees the atomicity and durability of the storage system. Delta lake relies on the following when interacting with storage systems.

 - **Atomic visibility :** Any file written through this store must be made visible, atomically means be visible entirely or not visible at all.
 - **Mutual exclusion :** Only one writer must be able to create a file at the final destination.
 - **Consistent listing :** Once a file has been written in a directory, it should offers ACID consistent listing of files.

Because storage systems do not necessarily provide all of these guarantees out-of-the-box. For that Delta Lake used the Log store API to provide the ACID guarantees for different storage systems, user can use different `LogStore` implementations.

[LogStore API code](https://github.com/delta-io/delta/blob/b76e2314583b0e2081a01163cea628031384b987/core/src/main/scala/io/delta/storage/LogStore.java#L69 "LogStore API code")

The `LogStore`, similar to Apache Spark, uses Hadoop FileSystem API to perform reads and writes. So Delta Lake supports concurrent reads on any storage system that provides an implementation of FileSystem API.

### Action performed on each transaction 

Each log record object contains an array of actions. Whenever a user performs an action like INSERT, DELETE, UPDATE or MERGE the Delta Lake breaks that operation down into series of below steps :

 - **Update metadata :** The metadata action changes the current metadata of the table. The metadata is a data structure containing the schema, partition column names and other configuration options, such as marking a table as append-only.
 - **Add file :** The add actions is used to add the file path into the log data structure. The add record for a data object can also include data statistics, such as the total record count and per-column min/max values and null counts.
 - **Remove file :** The remove actions is used to remove the file path from the log data structure. The remove action includes a timestamp that indicates when the removal occurred. Physical deletion of the data object can happen lazily after a user-specified retention time threshold.
 - **Set transaction :** To record own data inside log records, which can be useful for implementing end-to-end transactional application like structured streaming job has committed a micro-batch with the given ID and store appId and version fields in txn action.
 - **Change protocol :** The protocol action is used to increase the version of the Delta protocol that is required to read or write a given table.
 - **Commit info :** The commit info data structure contains the information of user commit means which operation was made, where, what time and etc.

**Let's read the first transaction log of version 0 and explore the schema**
```scala
	spark.read.json("delta_load_table/_delta_log/00000000000000000000.json").printSchema()
```
```json
root
 |-- add: struct (nullable = true)
 |    |-- dataChange: boolean (nullable = true)
 |    |-- modificationTime: long (nullable = true)
 |    |-- path: string (nullable = true)
 |    |-- size: long (nullable = true)
 |    |-- stats: string (nullable = true)
 |-- commitInfo: struct (nullable = true)
 |    |-- clusterId: string (nullable = true)
 |    |-- isBlindAppend: boolean (nullable = true)
 |    |-- isolationLevel: string (nullable = true)
 |    |-- notebook: struct (nullable = true)
 |    |    |-- notebookId: string (nullable = true)
 |    |-- operation: string (nullable = true)
 |    |-- operationParameters: struct (nullable = true)
 |    |    |-- description: string (nullable = true)
 |    |    |-- isManaged: string (nullable = true)
 |    |    |-- partitionBy: string (nullable = true)
 |    |    |-- properties: string (nullable = true)
 |    |-- timestamp: long (nullable = true)
 |    |-- userId: string (nullable = true)
 |    |-- userName: string (nullable = true)
 |-- metaData: struct (nullable = true)
 |    |-- createdTime: long (nullable = true)
 |    |-- format: struct (nullable = true)
 |    |    |-- provider: string (nullable = true)
 |    |-- id: string (nullable = true)
 |    |-- partitionColumns: array (nullable = true)
 |    |    |-- element: string (containsNull = true)
 |    |-- schemaString: string (nullable = true)
 |-- protocol: struct (nullable = true)
 |    |-- minReaderVersion: long (nullable = true)
 |    |-- minWriterVersion: long (nullable = true)

```


## ACID Transaction with Delta Lake
Delta Lake_'s transaction log.

The deltalog is a collection of ordered json files. It acts as a single source of truth giving to users access to the last version of a  `DeltaTable`'s state.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5NDE2NTE4NSw2MTk4NjI1OTIsLTE3NT
c0MjM0NDYsLTE4MTcyMTk0LDIxMTQyMTU1OTQsMTA0NjYyMTQs
LTEzMDU1MjM1NjcsLTE0NTk5Mjc1NzUsLTkzODUxMDYwMCwxMz
YyMzU4MTEyLDUyNTIwMTE3NywxMjI4Mjc5NjQyLDE3OTA2MzUw
NTUsMTQwMTM2ODc0MywtMTg3MDczNTk5MywtMTU2NDE1ODk3OC
wxOTEzNDQ3NzMwLDE5MDY0MjkzMDYsLTI2NDQ3NjgyMCwyNzA4
NDA2ODZdfQ==
-->