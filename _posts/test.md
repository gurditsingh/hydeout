## What is Spark Performance Tuning?

Spark Performance Tuning refers to the process of adjusting settings to record for memory, cores, and instances used by the system. This process guarantees that the Spark has a flawless performance and also prevents bottlenecking of resources in Spark.
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-tuning.jpg?raw=true)

 - **Data serialization** also determines a good network performance. You will be able to obtain good results in Spark performance by serialization. Spark supports two serialization libraries Java Serialization, Kryo Serialization.
 - **Memory Tuning** is necessary or important step in tuning. we need to give as much memory so that the entire dataset has to fit in memory.
 -  **Data Structure Tuning** One option to reduce memory consumption is by staying away from java features. Avoid the nested structure with lots of small objects and pointers. Instead of using strings for keys use numeric.
 -  **Garbage Collection Tuning** In order to avoid the large “churn” related to the RDDs that have been previously stored by the program, java will dismiss old objects in order to create space for new ones. However, by using data structures that feature fewer objects the cost is greatly reduced. One such example would be the employment an array of Ints instead of a linked list.
 -  **Memory Management** An efficient memory use is essential to good performance. Spark uses memory mainly for storage and execution. Storage memory is used to cache data that will be reused later. On the other hand, execution memory is used for computation in shuffles, sorts, joins, and aggregations.

## What we can Tune

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-tuning2.png?raw=true)

### Cluster Parameters

 - To apply any parameters first we need the information regarding the Cluster Size accordingly we can supply the parameters.
 - We need the information regarding the Instance type used in the Cluster like General Purpose, Compute-optimized, Memory-optimized, Storage-optimized and etc.
 - We can set the number of processors/cores so that we can choose the number of partitions/task of spark job.
 - We can set the memory size accordingly so that we can run the job in-memory and cache the data whenever required.
 - We need the information regarding the type of disk like SSD, RAM_DISK, HDD and etc. which can reduce the I/O operation and we can decide cache property like memory_only, memory_and_disk and etc.  

### Spark Configurations
Because of the in-memory nature of most Spark computations, Spark programs can be bottlenecked by any resource in the cluster: CPU, network bandwidth, or memory. 
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzY5OTk1NjUsMTg3Nzc2OTQ1NSwyMD
E0MDU3Nzg1LC0xMDU1ODE0ODA3LC0xNzc2NDE1Mzc0LDE2MDY5
MzYwOTcsNTg0NzczODM5LDE0MzcyOTE2NDUsLTIwODg3NDY2MT
IsMzkwODI3Njk3LC02NDA2ODg3NjUsNDU0MDk4MjkwLC0xMjQ1
NjE5MTE0LDE2Mjc4NTQwMTcsLTE3OTc3MDI2NDgsLTE2NTQzMD
AzNSw3ODYzODM0ODUsLTczMDM2MTMyNywtMjAzMDcwMjkyNiw1
Mzg4NTI5ODZdfQ==
-->