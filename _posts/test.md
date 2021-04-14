## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

 - **Executor Cores/Slots :** Slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine. On Executor there are cores/slots and those slots are available to insert tasks. The driver sends tasks to the vacant slots on the executors when there is work to be executed. This ties to distributing and parallelizing an execution thread.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"Task ==  slot  == core"**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"1 Task == 1 Partition == 1 slot == 1 core"**

 - **Executor Memory :**  Memory is divided into peak two types of memory primarily storage and the working memory. The Working memoty can be utilized and will be utilized by smart workloads unless there's a persistent object that consumes this storage workspace up to the configured amount which by default is 50% so half of the memory will be allocated for working memory and half of the memory will be allocated for for storage like persisted objects

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkzNDYyMjI3MSwtMTk5OTk1Njg5MCwyMD
g0ODM1NDg3LC0xNDE0ODA4Njg2LC03MzY0OTAyMzMsLTE3ODY2
MzcyMjksMzI5NTg4MzU2LDIwNDc2NTQ0NCwtNTg1NDIzNjgwLD
I4Mjk2NDg5MCwtMTMwNjYzNTI1OCwtNTE3MDcwNjI1LC0xODUy
NjU0MTA5LC0xNzgxNTIzMDUyLDgxOTQxNjU0NiwtMTIxMzc3OT
MwNCwtMTE3Nzg5ODIwMCwtMTU5Mjc3NjgzOSwtMTMzNDI3MzU1
MCwtNjAxMjMyODA0XX0=
-->