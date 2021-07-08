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
You can use the UPDATE operation to selectively update any rows that match a filtering condition, also known as a predicate. An SQL **UPDATE** statement changes the data of one or more records in a table. Either all the rows can be updated, or a subset may be chosen using a condition.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNDUyODk4ODAsMTkzMTg4NTQ5OCw1MT
Y2ODk1MjQsNDA1NjQwMzI1LDcwMDIzMDk2OCwyODAwNzMzMzEs
NTU0MjQ5MDUyLC0xMTE0ODQ2ODg1LDU3MzczODQ4OSwtNDA0OT
AzMjQxLDE2NDMzMTY1MSwtMTM4NzE5Nzk5MywxNTg3Mjk5OTAy
LC03NTkyMzE3NzgsOTYxMTU4Njc0LC0xNzM1MjcyNzIzLC0xND
EyMjE2MTAsMTExODczNDkxLDE5NjY1MTY3NjksODUxMzU3MTAy
XX0=
-->