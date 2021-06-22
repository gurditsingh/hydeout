
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
eyJoaXN0b3J5IjpbOTkyOTg0ODg5LC0xMTY4MDI0OTA5LDIxND
IzMTc2NzEsLTQyMTI0NDI3MywtMTcyMjQ3OTQyMiwtMTU3MTEx
NTYyMiwzMDE5ODAxODksLTIwMDQ1MTczMjIsLTE2NDMyNjE2ND
MsLTE5MjgwMDc0ODksNzQ3MDU5MDc5LDY3MTUyODUxNSwtNjkx
ODE3ODQ0LDEyNTUxMDg2LC0zMDIyMTM1NjksLTY2NzUxODUwMy
wtMTY3MDI4NTM3MiwyMDk1OTQ3NTc4LDEyNjAwMTIyMjMsMTI1
MDU1Njg1MF19
-->