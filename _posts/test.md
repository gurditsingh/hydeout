## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

 - **Executor Cores/Slots :** Slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine. On Executor there are cores/slots and those slots are available to insert tasks. The driver sends tasks to the vacant slots on the executors when there is work to be executed. This ties to distributing and parallelizing an execution thread.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"Task ==  slot  == core"**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"1 Task == 1 Partition == 1 slot == 1 core"**

 - **Executor Memory :**  

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NjkyNzc2OTcsLTE5OTk5NTY4OTAsMj
A4NDgzNTQ4NywtMTQxNDgwODY4NiwtNzM2NDkwMjMzLC0xNzg2
NjM3MjI5LDMyOTU4ODM1NiwyMDQ3NjU0NDQsLTU4NTQyMzY4MC
wyODI5NjQ4OTAsLTEzMDY2MzUyNTgsLTUxNzA3MDYyNSwtMTg1
MjY1NDEwOSwtMTc4MTUyMzA1Miw4MTk0MTY1NDYsLTEyMTM3Nz
kzMDQsLTExNzc4OTgyMDAsLTE1OTI3NzY4MzksLTEzMzQyNzM1
NTAsLTYwMTIzMjgwNF19
-->