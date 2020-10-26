

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc0NzMwNDQwNSwtMTk2NTIwNjYzLC0yMD
g4NzQ2NjEyLC0xMDMzNTc3MTcwLDk1Mzc3MTk1OCwzNTA2Nzkz
MzEsNTg3NjE2NTcsMzYyOTE1NzcxLDE0ODgzNDU4MjAsLTQ5Mz
MyMzYyNSwtMTI3ODQ2Njc3LC05OTkwMzAzMjIsLTE3MDY3MzE5
OTIsOTA3ODk3NzIyLC0xMzQzNTgwMDc2LC0xODcyNzU5NjU5LD
Y3OTMzMjM2NSwtNDAzOTc3NDYxLC0xNzMyMjM4Nzk4LC00NzE2
ODI4OTFdfQ==
-->