**Spark runs multiple tasks in parallel but not multiple jobs**
once a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel. **Hence, at a time, Spark runs multiple tasks in parallel but not multiple jobs.**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NjgwMDQ4ODEsLTIwODg3NDY2MTIsLT
EwMzM1NzcxNzAsOTUzNzcxOTU4LDM1MDY3OTMzMSw1ODc2MTY1
NywzNjI5MTU3NzEsMTQ4ODM0NTgyMCwtNDkzMzIzNjI1LC0xMj
c4NDY2NzcsLTk5OTAzMDMyMiwtMTcwNjczMTk5Miw5MDc4OTc3
MjIsLTEzNDM1ODAwNzYsLTE4NzI3NTk2NTksNjc5MzMyMzY1LC
00MDM5Nzc0NjEsLTE3MzIyMzg3OTgsMjAzNjY4NjYxMiw0Njg5
OTAyOTZdfQ==
-->