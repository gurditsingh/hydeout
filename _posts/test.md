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
	The below results shows the files which are added during the initial load in the transaction log (Query `select("add.path").where("add is not null"))`)
		![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt3.JPG?raw=true)

 2. **Append Data**
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
	In the append mode sample files are added by the Spark range function. The below results shows the files in the transaction log (Query `select("add.path").where("add is not null"))`)

	![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt4.JPG?raw=true)

 3. **Delete Data**

	```scala
	import io.delta.tables.DeltaTable

	DeltaTable.forPath("/FileStore/tables/deltaTimeTravel").delete("count == 2")
	```
	```scala
	display(spark.read.json("/FileStore/tables/deltaTimeTravel/_delta_log/00000000000000000002.json").select("remove.path").where("remove is not null"))
	```
	For the delete query we used DeltaTable API for simple delete the data from the Detla table. The below results shows the deleted files in the transaction log (Query `select("remove.path").where("removeis not null"))`)
	![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt5.JPG?raw=true)


## Working with Time Travel using 2 approaches
Every Operation in Delta table is automatically versioned and we can access any version of data. This allows to travel back to a different version of the delta table. Lets first see the history of the Delta table.
```scala
import io.delta.tables.DeltaTable

display(DeltaTable.forPath("/FileStore/tables/deltaTimeTravel").history())
```

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt7.JPG?raw=true)

 ### 1. Using with Timestamp
You can provide the timestamp or date string as an option to the DataFrame reader. User can see the history and select the appropriated version of the Delta table.

First Version of Delta table (Initial load)
```scala
spark.read.format("delta").option("timestampAsOf","2021-07-02T10:26:40.000+0000").load(target_path).count()

res29: Long = 52
```
Second Version of Delta table (Append)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNjA2NTQ2OCwxNTg3Mjk5OTAyLC03NT
kyMzE3NzgsOTYxMTU4Njc0LC0xNzM1MjcyNzIzLC0xNDEyMjE2
MTAsMTExODczNDkxLDE5NjY1MTY3NjksODUxMzU3MTAyLC0xNT
U3ODMxNjY5LC0xMjE1Njk0MjEzLC0xNDMxMTAzMjgyLC0xNzIw
NDMwMzkyLC0yMDg4NzQ2NjEyLC0xNTc0NjI4NjIxLC03NjY0NT
AxNjQsODY1NTY3NjYyLDUyMzIxMjc0NywtMTgwMDUyNzI5Miwt
MTI5MDQyMDk3Nl19
-->