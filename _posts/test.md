## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

 - **Executor Cores/Slots :** Slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine. On Executor there are cores/slots and those slots are available to insert tasks. The driver sends tasks to the vacant slots on the executors when there is work to be executed. This ties to distributing and parallelizing an execution thread.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"Task ==  slot  == core"**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"1 Task == 1 Partition == 1 slot == 1 core"**

 - **Executor Memory :**  Memory is divided into peak two types of memory primarily storage and the working memory. The working memory will be utilized for actual execution or smart workloads. The storage memory used for persistent objects. these memory can be configured, which by default is 50% so half of the memory will be allocated for working memory and half of the memory will be allocated for for storage like persisted objects.
 - **Local Memory :** Every executor has disks. We know SPARK is an in-memory solution but we still have to have disks the disks are attached directly and those provide space for shuffle partitions and  shuffle stages and they also provide space for persistence to disk and spills from the executor from the execution of the workload the disks have attributes right we have fast disks we have slow disks we have remote and local the types of disks that are attached to your cluster

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3NDc0NDE5NSwzODkwMTQxLC0xOTk5OT
U2ODkwLDIwODQ4MzU0ODcsLTE0MTQ4MDg2ODYsLTczNjQ5MDIz
MywtMTc4NjYzNzIyOSwzMjk1ODgzNTYsMjA0NzY1NDQ0LC01OD
U0MjM2ODAsMjgyOTY0ODkwLC0xMzA2NjM1MjU4LC01MTcwNzA2
MjUsLTE4NTI2NTQxMDksLTE3ODE1MjMwNTIsODE5NDE2NTQ2LC
0xMjEzNzc5MzA0LC0xMTc3ODk4MjAwLC0xNTkyNzc2ODM5LC0x
MzM0MjczNTUwXX0=
-->