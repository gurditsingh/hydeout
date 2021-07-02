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

	![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_tt1.JPG?raw=true)

 2. List item

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NzE5NzY1MTksMTk2NjUxNjc2OSw4NT
EzNTcxMDIsLTE1NTc4MzE2NjksLTEyMTU2OTQyMTMsLTE0MzEx
MDMyODIsLTE3MjA0MzAzOTIsLTIwODg3NDY2MTIsLTE1NzQ2Mj
g2MjEsLTc2NjQ1MDE2NCw4NjU1Njc2NjIsNTIzMjEyNzQ3LC0x
ODAwNTI3MjkyLC0xMjkwNDIwOTc2LC0xODgxMzU4MDM3LDg1Nz
A5OTIyMCwtMTg0MDkxMjY1OCwxMzkwMjczNDA3LC0xNDkwNzY0
NDc1LC00NDQ4NzU1ODNdfQ==
-->