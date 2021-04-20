## What is Data Skew?
Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregatio, however, Spark distributes the data by join key, so that data from the two tables being joined will be in the same task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzYzMTQwOTAsODM5ODM0MjkxLDE4MTA4MD
MzNTcsMTg3MTM1NDkwNCwxMTI5NDM4Nzg1LDExMjk3OTA4MjYs
MTUzODIzMzMyNCwtMjA3MDIzMzg2Niw0MDE3OTI5MTEsNzE2NT
IwMDg4LC0zNjY4MDQ1MDMsLTE3MDA0MjgzMDEsMTUxMjQ4NTMw
OCwxMjc2ODU2MjYsLTIwMjcxOTc5ODUsMTQwMTY4NjY2MiwtMT
E0MDE5MjQ5NywtNTIzMDIxNzgzLC0yNTQxNjI2NSwtMTI5ODI5
NjQ5Nl19
-->