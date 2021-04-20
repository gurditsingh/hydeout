## What is Data Skew?
Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjIyMTk3MTk2LDgzOTgzNDI5MSwxODEwOD
AzMzU3LDE4NzEzNTQ5MDQsMTEyOTQzODc4NSwxMTI5NzkwODI2
LDE1MzgyMzMzMjQsLTIwNzAyMzM4NjYsNDAxNzkyOTExLDcxNj
UyMDA4OCwtMzY2ODA0NTAzLC0xNzAwNDI4MzAxLDE1MTI0ODUz
MDgsMTI3Njg1NjI2LC0yMDI3MTk3OTg1LDE0MDE2ODY2NjIsLT
ExNDAxOTI0OTcsLTUyMzAyMTc4MywtMjU0MTYyNjUsLTEyOTgy
OTY0OTZdfQ==
-->