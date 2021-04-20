## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.

### For Example :


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ4Njk2OTk4MiwtNTM5NjgwNDE0LDgzOT
gzNDI5MSwxODcxMzU0OTA0LDExMjk0Mzg3ODUsMTEyOTc5MDgy
NiwxNTM4MjMzMzI0LC0yMDcwMjMzODY2LDQwMTc5MjkxMSw3MT
Y1MjAwODgsLTM2NjgwNDUwMywtMTcwMDQyODMwMSwxNTEyNDg1
MzA4LDEyNzY4NTYyNiwtMjAyNzE5Nzk4NSwxNDAxNjg2NjYyLC
0xMTQwMTkyNDk3LC01MjMwMjE3ODMsLTI1NDE2MjY1LC0xMjk4
Mjk2NDk2XX0=
-->