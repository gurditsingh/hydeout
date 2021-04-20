## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUzOTY4MDQxNCw4Mzk4MzQyOTEsMTg3MT
M1NDkwNCwxMTI5NDM4Nzg1LDExMjk3OTA4MjYsMTUzODIzMzMy
NCwtMjA3MDIzMzg2Niw0MDE3OTI5MTEsNzE2NTIwMDg4LC0zNj
Y4MDQ1MDMsLTE3MDA0MjgzMDEsMTUxMjQ4NTMwOCwxMjc2ODU2
MjYsLTIwMjcxOTc5ODUsMTQwMTY4NjY2MiwtMTE0MDE5MjQ5Ny
wtNTIzMDIxNzgzLC0yNTQxNjI2NSwtMTI5ODI5NjQ5Niw0MjE5
MzA1ODBdfQ==
-->