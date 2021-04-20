## What is Data Skew?
Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregatio, however, Spark distributes the data by join key, so that data from the two tables being joined will be in the same task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzYzMTQwOTAsODM5ODM0MjkxLDE4NzEzNT
Q5MDQsMTEyOTQzODc4NSwxMTI5NzkwODI2LDE1MzgyMzMzMjQs
LTIwNzAyMzM4NjYsNDAxNzkyOTExLDcxNjUyMDA4OCwtMzY2OD
A0NTAzLC0xNzAwNDI4MzAxLDE1MTI0ODUzMDgsMTI3Njg1NjI2
LC0yMDI3MTk3OTg1LDE0MDE2ODY2NjIsLTExNDAxOTI0OTcsLT
UyMzAyMTc4MywtMjU0MTYyNjUsLTEyOTgyOTY0OTYsNDIxOTMw
NTgwXX0=
-->