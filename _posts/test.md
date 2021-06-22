
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - Delta Lake facilitates Scheme Evolution which allow to users to easily change the table schema to accommodate the new data with new schema (either add new columns or remove old columns).
 

# Lets first examine the Schema Enforcement

## Schema Enforcement

In Delta Lake the schema enforcement also known as schema validation which in ensure the data quality in delta lake tables. Delta Lake uses schema validation/enforcement on write. When any new data comes first its checked for data compatibility with with the target table schema at the time of writing. If the schema is not matched with the target table Delta Lake reject the transaction and raise the exception schema mismatch.

 To determine whether the schema is compatible, Delta Lake uses the following there rule:
 
 - Delta Lake ensure that no addional columns present in data with respect to table schema.
 - Delta Lake ensure the  data type for each column with respect to table schema.
 - Delta Lake ensure the column names with respect to table schema.

### Let's Understand the Schema Enforcement by two ways

 1. **How Schema Enforcement works with parquet format**
 
	 Let first create a new parquet table with the parquet file.
	```scala
	val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
	val target_path ="/FileStore/tables/parquetSchemaEnforcement"

	spark.read.parquet(source_path).write.format("parquet").save(target_path)
	spark.read.parquet(target_path).createOrReplaceTempView("parquet_tbl")
	```
Next print the schema of the parquet table.
```scala
spark.read.format("parquet").load(target_path).printSchema

root
 |-- state: string (nullable = true)
 |-- count: integer (nullable = true)

```
Next lets check how many rows are in the table. Perform count operation on the parquet table.
```scala
spark.sql("select count(*) from parquet_tbl").show()

+--------+
|count(1)|
+--------+
|      52|
+--------+

```
Next Let start appending some new data to it using Structured Streaming into the parquet table. We will generate a stream of data from with randomly generated states and dummy count.



![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5NzE3MzkzMSw5OTI5ODQ4ODksLTExNj
gwMjQ5MDksMjE0MjMxNzY3MSwtNDIxMjQ0MjczLC0xNzIyNDc5
NDIyLC0xNTcxMTE1NjIyLDMwMTk4MDE4OSwtMjAwNDUxNzMyMi
wtMTY0MzI2MTY0MywtMTkyODAwNzQ4OSw3NDcwNTkwNzksNjcx
NTI4NTE1LC02OTE4MTc4NDQsMTI1NTEwODYsLTMwMjIxMzU2OS
wtNjY3NTE4NTAzLC0xNjcwMjg1MzcyLDIwOTU5NDc1NzgsMTI2
MDAxMjIyM119
-->