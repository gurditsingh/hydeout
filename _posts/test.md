## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. Delta lake provide a data management like functionality in which you do easy audit, roll back of bad data and reproduce the data.

## Lets first create a Delta table
```scala
val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
val target_path ="/FileStore/tables/deltaTimeTravel"

spark.read.parquet(source_path).write.format("delta").save(target_path)
spark.read.format("delta").load(target_path)
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbNDcwMDQ0NjcwLDE5NjY1MTY3NjksODUxMz
U3MTAyLC0xNTU3ODMxNjY5LC0xMjE1Njk0MjEzLC0xNDMxMTAz
MjgyLC0xNzIwNDMwMzkyLC0yMDg4NzQ2NjEyLC0xNTc0NjI4Nj
IxLC03NjY0NTAxNjQsODY1NTY3NjYyLDUyMzIxMjc0NywtMTgw
MDUyNzI5MiwtMTI5MDQyMDk3NiwtMTg4MTM1ODAzNyw4NTcwOT
kyMjAsLTE4NDA5MTI2NTgsMTM5MDI3MzQwNywtMTQ5MDc2NDQ3
NSwtNDQ0ODc1NTgzXX0=
-->