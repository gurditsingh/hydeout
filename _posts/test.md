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
In the below res
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


```scala
import io.delta.tables.DeltaTable

DeltaTable.forPath("/FileStore/tables/deltaTimeTravel").delete("count == 2")
```
```scala
display(spark.read.json("/FileStore/tables/deltaTimeTravel/_delta_log/00000000000000000002.json").select("remove.path").where("remove is not null"))
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE5ODg1MDQ1OSwtMTczNTI3MjcyMywtMT
QxMjIxNjEwLDExMTg3MzQ5MSwxOTY2NTE2NzY5LDg1MTM1NzEw
MiwtMTU1NzgzMTY2OSwtMTIxNTY5NDIxMywtMTQzMTEwMzI4Mi
wtMTcyMDQzMDM5MiwtMjA4ODc0NjYxMiwtMTU3NDYyODYyMSwt
NzY2NDUwMTY0LDg2NTU2NzY2Miw1MjMyMTI3NDcsLTE4MDA1Mj
cyOTIsLTEyOTA0MjA5NzYsLTE4ODEzNTgwMzcsODU3MDk5MjIw
LC0xODQwOTEyNjU4XX0=
-->