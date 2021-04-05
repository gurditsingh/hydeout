## What is Spark Performance Tuning?

Spark Performance Tuning refers to the process of adjusting settings to record for memory, cores, and instances used by the system. This process guarantees that the Spark has a flawless performance and also prevents bottlenecking of resources in Spark.
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-tuning.jpg?raw=true)

 - **Data serialization** also determines a good network performance. You will be able to obtain good results in Spark performance by serialization. Spark supports two serialization libraries Java Serialization, Kryo Serialization.
 - **Memory Tuning** is necessary or important step in tuning. we need to give as much memory so that the entire dataset has to fit in memory.
 -  **Data Structure Tuning** One option to reduce memory consumption is by staying away from java features. Avoid the nested structure with lots of small objects and pointers. Instead of using strings for keys use numeric.
 -  **Garbage Collection Tuning** In order to avoid the large “churn” related to the RDDs that have been previously stored by the program, java will dismiss old objects in order to create space for new ones. However, by using data structures that feature fewer objects the cost is greatly reduced. One such example would be the employment an array of Ints instead of a linked list.
 -  **Memory Management** An efficient memory use is essential to good performance. Spark uses memory mainly for storage and execution. Storage memory is used to cache data that will be reused later. On the other hand, execution memory is used for computation in shuffles, sorts, joins, and aggregations.


![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-tuning.jpg?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbODkxNDUwMjI1LDE2MDY5MzYwOTcsNTg0Nz
czODM5LDE0MzcyOTE2NDUsLTIwODg3NDY2MTIsMzkwODI3Njk3
LC02NDA2ODg3NjUsNDU0MDk4MjkwLC0xMjQ1NjE5MTE0LDE2Mj
c4NTQwMTcsLTE3OTc3MDI2NDgsLTE2NTQzMDAzNSw3ODYzODM0
ODUsLTczMDM2MTMyNywtMjAzMDcwMjkyNiw1Mzg4NTI5ODYsMj
c0NTcxMjA3LDEwODI5MDM2MDksMTcwMDU5OTU1MCwxNTk3OTA2
ODBdfQ==
-->