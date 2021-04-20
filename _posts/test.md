## What is Data Skew?
Data skew happens when for one reason or another, a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join, however, Spark distributes the data by join key, so that data from the two tables being joined will be in the same task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjY4ODI1OTU0LDE4NzEzNTQ5MDQsMTEyOT
QzODc4NSwxMTI5NzkwODI2LDE1MzgyMzMzMjQsLTIwNzAyMzM4
NjYsNDAxNzkyOTExLDcxNjUyMDA4OCwtMzY2ODA0NTAzLC0xNz
AwNDI4MzAxLDE1MTI0ODUzMDgsMTI3Njg1NjI2LC0yMDI3MTk3
OTg1LDE0MDE2ODY2NjIsLTExNDAxOTI0OTcsLTUyMzAyMTc4My
wtMjU0MTYyNjUsLTEyOTgyOTY0OTYsNDIxOTMwNTgwLC0yMTQ1
NzA2MTYyXX0=
-->