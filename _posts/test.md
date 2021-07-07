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

	

## Delta Lake : UPDATE


















![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_t7.JPG?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg3MTMzMDk0NCw3MDAyMzA5NjgsMjgwMD
czMzMxLDU1NDI0OTA1MiwtMTExNDg0Njg4NSw1NzM3Mzg0ODks
LTQwNDkwMzI0MSwxNjQzMzE2NTEsLTEzODcxOTc5OTMsMTU4Nz
I5OTkwMiwtNzU5MjMxNzc4LDk2MTE1ODY3NCwtMTczNTI3Mjcy
MywtMTQxMjIxNjEwLDExMTg3MzQ5MSwxOTY2NTE2NzY5LDg1MT
M1NzEwMiwtMTU1NzgzMTY2OSwtMTIxNTY5NDIxMywtMTQzMTEw
MzI4Ml19
-->