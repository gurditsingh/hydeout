## Problem
Data lakes holds large amount of data, and on these data needs to perform updates, merge and delete over the times. With the traditional data lakes it difficult to perform such a simple operations (because no one supports ACID). So that the user need to build there own strategy to perform these operations but in this approach data consistency is big threat, and it can become very difficult for data engineering and data scientists to reason about their data.

## Solution
Delta Lake solves this issue by enabling data analysts to easily query all the data in their data lake using SQL. Then, data engineering or data scientists can perform update, merge or delete on the data using SQL or programmatically, because to Delta Lake supports ACID transactions.


## What is DML Operation
DML refers to "Data Manipulation Language", a subset of SQL statements which deals with data manipulation. A transaction is a sequence of one or more SQL statements that can SELECT, INSERT, UPDATE, DELETE the data.

## Lets first create a Delta table
```scala
val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
val target_path ="/FileStore/tables/deltaTimeTravel"

spark.read.parquet(source_path).write.format("delta").save(target_path)
spark.read.format("delta").load(target_path)
```

	

## Delta Lake : UPDATE


















![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_t7.JPG?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzAwMjMwOTY4LDI4MDA3MzMzMSw1NTQyND
kwNTIsLTExMTQ4NDY4ODUsNTczNzM4NDg5LC00MDQ5MDMyNDEs
MTY0MzMxNjUxLC0xMzg3MTk3OTkzLDE1ODcyOTk5MDIsLTc1OT
IzMTc3OCw5NjExNTg2NzQsLTE3MzUyNzI3MjMsLTE0MTIyMTYx
MCwxMTE4NzM0OTEsMTk2NjUxNjc2OSw4NTEzNTcxMDIsLTE1NT
c4MzE2NjksLTEyMTU2OTQyMTMsLTE0MzExMDMyODIsLTE3MjA0
MzAzOTJdfQ==
-->