

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

**It does not mean spark cannot run concurrent jobs**
By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.


<!--stackedit_data:
eyJoaXN0b3J5IjpbOTg0MzQzNTU3LC0xODA1NjA5MDQ3LC03ND
czMDQ0MDUsLTE5NjUyMDY2MywtMjA4ODc0NjYxMiwtMTAzMzU3
NzE3MCw5NTM3NzE5NTgsMzUwNjc5MzMxLDU4NzYxNjU3LDM2Mj
kxNTc3MSwxNDg4MzQ1ODIwLC00OTMzMjM2MjUsLTEyNzg0NjY3
NywtOTk5MDMwMzIyLC0xNzA2NzMxOTkyLDkwNzg5NzcyMiwtMT
M0MzU4MDA3NiwtMTg3Mjc1OTY1OSw2NzkzMzIzNjUsLTQwMzk3
NzQ2MV19
-->