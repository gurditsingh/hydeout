

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MDU2MDkwNDcsLTc0NzMwNDQwNSwtMT
k2NTIwNjYzLC0yMDg4NzQ2NjEyLC0xMDMzNTc3MTcwLDk1Mzc3
MTk1OCwzNTA2NzkzMzEsNTg3NjE2NTcsMzYyOTE1NzcxLDE0OD
gzNDU4MjAsLTQ5MzMyMzYyNSwtMTI3ODQ2Njc3LC05OTkwMzAz
MjIsLTE3MDY3MzE5OTIsOTA3ODk3NzIyLC0xMzQzNTgwMDc2LC
0xODcyNzU5NjU5LDY3OTMzMjM2NSwtNDAzOTc3NDYxLC0xNzMy
MjM4Nzk4XX0=
-->