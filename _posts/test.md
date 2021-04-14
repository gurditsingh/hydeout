## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.
 <br />
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)

 - **Executor Cores/Slots :** Slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine. On Executor there are cores/slots and those slots are available to insert tasks. The driver sends tasks to the vacant slots on the executors when there is work to be executed. This ties to distributing and parallelizing an execution thread.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"Task ==  slot  == core"**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **"1 Task == 1 Partition == 1 slot == 1 core"**

 - **Executor Memory :**  Memory is divided into peak two types of memory primarily storage and the working memory. The working memory will be utilized for actual execution or smart workloads. The storage memory used for persistent objects. these memory can be configured, which by default is 50% so half of the memory will be allocated for working memory and half of the memory will be allocated for for storage like persisted objects.
 - **Local Memory :** Every executor has disks. We know SPARK is an in-memory solution but we still have to have disks. The disks provide space for shuffle partitions and shuffle stages and they also provide space for persistence to disk and spills from the executor. The disks have attributes right we have fast disks we have slow disks. We have remote and local the types of disks that are attached to your cluster.

## Spark Memory Management

 - Spark is an in-memory processing engine spark takes data in-memory and process it.
 - Allocation and usage of the memory plays a vital role in your spark application. suppose you write a good spark application but you haven't provide and allocate the required memory to your application. The application may got delayed or failed due to OOM.
 - Efficient memory use is critical for good performance because of that your application may not meet the SLA's.
 - The memory management is an important aspect for the spark application because application generates intermediate state while executing the tasks.

Memory usage is spark largely falls under the below categories:

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_memory_mg.png?raw=true)
 

 - **Reserve Memory :** This is the memory reserved by the system, and its size is hardcoded in the spark code. Tts value is 300MB, which means that this 300MB of RAM does not participate in Spark memory region size calculations, and its size cannot be changed in any way without Spark code recompilation or setting  _spark.testing.reservedMemory_, which is not recommended as it is a testing parameter not intended to be used in production. Be aware, this memory is only called “reserved”, in fact it is not used by Spark in any way.

## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyOTM1MjY4NjAsLTEyOTgyOTY0OTYsND
IxOTMwNTgwLC0yMTQ1NzA2MTYyLDM4OTAxNDEsLTE5OTk5NTY4
OTAsMjA4NDgzNTQ4NywtMTQxNDgwODY4NiwtNzM2NDkwMjMzLC
0xNzg2NjM3MjI5LDMyOTU4ODM1NiwyMDQ3NjU0NDQsLTU4NTQy
MzY4MCwyODI5NjQ4OTAsLTEzMDY2MzUyNTgsLTUxNzA3MDYyNS
wtMTg1MjY1NDEwOSwtMTc4MTUyMzA1Miw4MTk0MTY1NDYsLTEy
MTM3NzkzMDRdfQ==
-->