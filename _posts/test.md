## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.

### For Example :
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-data-skew.png?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTY0ODAyMjM5LC01Mzk2ODA0MTQsODM5OD
M0MjkxLDE4NzEzNTQ5MDQsMTEyOTQzODc4NSwxMTI5NzkwODI2
LDE1MzgyMzMzMjQsLTIwNzAyMzM4NjYsNDAxNzkyOTExLDcxNj
UyMDA4OCwtMzY2ODA0NTAzLC0xNzAwNDI4MzAxLDE1MTI0ODUz
MDgsMTI3Njg1NjI2LC0yMDI3MTk3OTg1LDE0MDE2ODY2NjIsLT
ExNDAxOTI0OTcsLTUyMzAyMTc4MywtMjU0MTYyNjUsLTEyOTgy
OTY0OTZdfQ==
-->