## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.

### For Example :
Suppose we have four partitions of data as below and when they come in at 128 MB each they are roughly the same size in terms of number of records and number of MBs. However, once we perform a group by city, the first 3 cities are roughly uniform but the last city is significantly larger than other cities which results in a data skewness (uneven distribution of records in partitions)

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-data-skew.png?raw=true)

 - The skewed partition/task (City D) will take more time as compared to other cities.
 - The skewed task take more memory as compared to other cities.
 - The single skewed task will impact the whole stage. because spark execute 4 partitions/task simultaneously and wait to complete the whole stage.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU1OTQ3NjczMywtNTM5NjgwNDE0LDgzOT
gzNDI5MSwxODcxMzU0OTA0LDExMjk0Mzg3ODUsMTEyOTc5MDgy
NiwxNTM4MjMzMzI0LC0yMDcwMjMzODY2LDQwMTc5MjkxMSw3MT
Y1MjAwODgsLTM2NjgwNDUwMywtMTcwMDQyODMwMSwxNTEyNDg1
MzA4LDEyNzY4NTYyNiwtMjAyNzE5Nzk4NSwxNDAxNjg2NjYyLC
0xMTQwMTkyNDk3LC01MjMwMjE3ODMsLTI1NDE2MjY1LC0xMjk4
Mjk2NDk2XX0=
-->