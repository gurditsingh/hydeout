**Spark runs multiple tasks in parallel but not multiple jobs**
once a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**WARNING: We used the word ‘job’ for ‘spark action’. In this we refer 'Job' as 'Spark Action' It does not mean spark cannot run concurrent jobs.**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MjQwMzMyNTksLTE5NjUyMDY2MywtMj
A4ODc0NjYxMiwtMTAzMzU3NzE3MCw5NTM3NzE5NTgsMzUwNjc5
MzMxLDU4NzYxNjU3LDM2MjkxNTc3MSwxNDg4MzQ1ODIwLC00OT
MzMjM2MjUsLTEyNzg0NjY3NywtOTk5MDMwMzIyLC0xNzA2NzMx
OTkyLDkwNzg5NzcyMiwtMTM0MzU4MDA3NiwtMTg3Mjc1OTY1OS
w2NzkzMzIzNjUsLTQwMzk3NzQ2MSwtMTczMjIzODc5OCwtNDcx
NjgyODkxXX0=
-->