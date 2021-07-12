## Problem
Data lakes holds large amount of data, and on these data needs to perform updates, merge and delete over the times. With the traditional data lakes it difficult to perform such a simple operations (because no one supports ACID). So that the user need to build there own strategy to perform these operations but in this approach data consistency is big threat, and it can become very difficult for data engineering and data scientists to reason about their data.

## Solution
Delta Lake solves this issue by enabling data analysts to easily query all the data in their data lake using SQL. Then, data engineering or data scientists can perform update, merge or delete on the data using SQL or programmatically, because to Delta Lake supports ACID transactions.


## What is DML Operation
DML refers to "Data Manipulation Language", a subset of SQL statements which deals with data manipulation. A transaction is a sequence of one or more SQL statements that can SELECT, INSERT, UPDATE, DELETE the data.

## Lets first create a Delta table
```scala
dbutils.fs.rm("/FileStore/tables/deltaDML",true)
val source_path = "/FileStore/tables/data/test_data_snappy.parquet"
val target_path ="/FileStore/tables/deltaDML"

spark.read.parquet(source_path).write.format("delta").save(target_path)
spark.read.format("delta").load(target_path).createOrReplaceTempView("delta_dml_tbl")
```

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep6_dml1.JPG?raw=true)

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep6_dml4.JPG?raw=true)



## Delta Lake : UPDATE
You can use the UPDATE operation to selectively update any rows that match a filtering condition, also known as a predicate. An SQL **UPDATE** statement changes the data of one or more records in a table. Either all the rows can be updated, or a subset may be chosen using a condition.

**Update by SQL query**
```sql
UPDATE delta_dml_tbl SET p_count = "550" WHERE p_id = 'p5'
```
**Update by Scala programmatically**
```scala
import io.delta.tables.DeltaTable

val dt = DeltaTable.forPath(target_path)
dt.updateExpr("p_id == 'p5'",Map("p_count"->"550"))
```

### how update works internally
Delta Lake maintains these files under the hood. As above created delta table has version 0 of the table where it have four files. Now, lets say you run Update. What it will do underneath is that it will use two scans on this data, to update detla table.

 1. First Scan :
![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep6_dml.JPG?raw=true)
	 - First it will do a scan the files that contains the data that needs to be updated based on the predicate.
	 - let's say out of four files, two of the files has data that matches the predicate. Delta stores the data as parquet files.
	 - So now not all the rows in the parquet files may match the data, so there'll be some rows that actually match the predicate, some rows that does not match the predicate,
	 - Delta Lake uses **data skipping** whenever possible to speed up this process.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzc0NDE2ODAyLC0xNTM2NTEwODQ1LC0xNT
M2NTEwODQ1LC0xMjM0NDcwMjI3LC0xNDIwNTU4NTU5LC0xMTI2
ODYzMTI3LC0xMTQ1Mjg5ODgwLDE5MzE4ODU0OTgsNTE2Njg5NT
I0LDQwNTY0MDMyNSw3MDAyMzA5NjgsMjgwMDczMzMxLDU1NDI0
OTA1MiwtMTExNDg0Njg4NSw1NzM3Mzg0ODksLTQwNDkwMzI0MS
wxNjQzMzE2NTEsLTEzODcxOTc5OTMsMTU4NzI5OTkwMiwtNzU5
MjMxNzc4XX0=
-->