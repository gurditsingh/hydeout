## What is Data Skew?
Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjIyMTk3MTk2LDgzOTgzNDI5MSwxODcxMz
U0OTA0LDExMjk0Mzg3ODUsMTEyOTc5MDgyNiwxNTM4MjMzMzI0
LC0yMDcwMjMzODY2LDQwMTc5MjkxMSw3MTY1MjAwODgsLTM2Nj
gwNDUwMywtMTcwMDQyODMwMSwxNTEyNDg1MzA4LDEyNzY4NTYy
NiwtMjAyNzE5Nzk4NSwxNDAxNjg2NjYyLC0xMTQwMTkyNDk3LC
01MjMwMjE3ODMsLTI1NDE2MjY1LC0xMjk4Mjk2NDk2LDQyMTkz
MDU4MF19
-->