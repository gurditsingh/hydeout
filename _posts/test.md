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

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep6_dml3.JPG?raw=true)



## Delta Lake : UPDATE
You can use the UPDATE operation to selectively update any rows that match a filtering condition, also known as a predicate. The code below demonstrates how to use each type of predicate as part of an UPDATE statement.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTE2Njg5NTI0LDQwNTY0MDMyNSw3MDAyMz
A5NjgsMjgwMDczMzMxLDU1NDI0OTA1MiwtMTExNDg0Njg4NSw1
NzM3Mzg0ODksLTQwNDkwMzI0MSwxNjQzMzE2NTEsLTEzODcxOT
c5OTMsMTU4NzI5OTkwMiwtNzU5MjMxNzc4LDk2MTE1ODY3NCwt
MTczNTI3MjcyMywtMTQxMjIxNjEwLDExMTg3MzQ5MSwxOTY2NT
E2NzY5LDg1MTM1NzEwMiwtMTU1NzgzMTY2OSwtMTIxNTY5NDIx
M119
-->