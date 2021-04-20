## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.

### For Example :
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4MDY4NDg5LC01Mzk2ODA0MTQsODM5OD
M0MjkxLDE4MTA4MDMzNTcsMTg3MTM1NDkwNCwxMTI5NDM4Nzg1
LDExMjk3OTA4MjYsMTUzODIzMzMyNCwtMjA3MDIzMzg2Niw0MD
E3OTI5MTEsNzE2NTIwMDg4LC0zNjY4MDQ1MDMsLTE3MDA0Mjgz
MDEsMTUxMjQ4NTMwOCwxMjc2ODU2MjYsLTIwMjcxOTc5ODUsMT
QwMTY4NjY2MiwtMTE0MDE5MjQ5NywtNTIzMDIxNzgzLC0yNTQx
NjI2NV19
-->