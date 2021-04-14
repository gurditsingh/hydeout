## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

 - **Executor Cores/Slots** : slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine. On Executor there are cores/slots and those slots are available to insert tasks. The driver sends tasks to the vacant s_lots_ on the _executors_ when there is work to be executed. This ties to distributing and parallelizing an execution thread.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyMTUxNzYwNCwtMTk5OTk1Njg5MCwyMD
g0ODM1NDg3LC0xNDE0ODA4Njg2LC03MzY0OTAyMzMsLTE3ODY2
MzcyMjksMzI5NTg4MzU2LDIwNDc2NTQ0NCwtNTg1NDIzNjgwLD
I4Mjk2NDg5MCwtMTMwNjYzNTI1OCwtNTE3MDcwNjI1LC0xODUy
NjU0MTA5LC0xNzgxNTIzMDUyLDgxOTQxNjU0NiwtMTIxMzc3OT
MwNCwtMTE3Nzg5ODIwMCwtMTU5Mjc3NjgzOSwtMTMzNDI3MzU1
MCwtNjAxMjMyODA0XX0=
-->