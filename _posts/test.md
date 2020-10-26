

**Spark runs multiple tasks in parallel but not multiple jobs:**
When a spark action is invoked, a spark job comes into existence which consists of one or more stages and further these stages are broken down into numerous tasks which are worked upon by the executors in parallel but spark not run multiple jobs in parallel when multiple action are called.**

**NOTE: We used the word ‘job’ for ‘spark action’.**

By running concurrent jobs with a single spark session, will not only maximise the resource utilisation but also reduce application time and cost drastically. Furthermore, if we have adequate resources and these jobs do not have any interlink between them then it does not make sense to execute them in a loop or as a different spark applications.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTg4NTQ2MywtNzQ3MzA0NDA1LC0xOT
Y1MjA2NjMsLTIwODg3NDY2MTIsLTEwMzM1NzcxNzAsOTUzNzcx
OTU4LDM1MDY3OTMzMSw1ODc2MTY1NywzNjI5MTU3NzEsMTQ4OD
M0NTgyMCwtNDkzMzIzNjI1LC0xMjc4NDY2NzcsLTk5OTAzMDMy
MiwtMTcwNjczMTk5Miw5MDc4OTc3MjIsLTEzNDM1ODAwNzYsLT
E4NzI3NTk2NTksNjc5MzMyMzY1LC00MDM5Nzc0NjEsLTE3MzIy
Mzg3OThdfQ==
-->