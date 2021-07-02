## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. Delta lake provide a data management like functionality in which you do easy audit, roll back of bad data and reproduce the data.

## Lets first create a Delta table

 1. **Initial Load** 

	```scala
	val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
	val target_path ="/FileStore/tables/deltaTimeTravel"

	spark.read.parquet(source_path).write.format("delta").save(target_path)
	spark.read.format("delta").load(target_path)
	```
	```scala
	display(spark.read.json("/FileStore/tables/deltaTimeTravel/_delta_log/00000000000000000000.json").select("add.path").where("add is not null"))
	```

	![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt3.JPG?raw=true)

 2. **Append More Data**
```scala
import org.apache.spark.sql.functions._

spark.range(5)
.withColumn("state",lit("N/A"))
.withColumn("count",lit(2))
.select("state","count")
.write.format("delta").mode("append").save(target_path)
```
```scala
display(spark.read.json("/FileStore/tables/deltaTimeTravel/_delta_log/00000000000000000001.json").select("add.path").where("add is not null"))
```
![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt4.JPG?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MzUyNzI3MjMsLTE0MTIyMTYxMCwxMT
E4NzM0OTEsMTk2NjUxNjc2OSw4NTEzNTcxMDIsLTE1NTc4MzE2
NjksLTEyMTU2OTQyMTMsLTE0MzExMDMyODIsLTE3MjA0MzAzOT
IsLTIwODg3NDY2MTIsLTE1NzQ2Mjg2MjEsLTc2NjQ1MDE2NCw4
NjU1Njc2NjIsNTIzMjEyNzQ3LC0xODAwNTI3MjkyLC0xMjkwND
IwOTc2LC0xODgxMzU4MDM3LDg1NzA5OTIyMCwtMTg0MDkxMjY1
OCwxMzkwMjczNDA3XX0=
-->