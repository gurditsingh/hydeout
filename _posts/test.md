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

### Cluster Parameters:

 - To apply any parameters first we need the information regarding the Cluster Size accordingly we can supply the parameters.
 - We need the information 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NzI5NDY0MDMsMTYwNjkzNjA5Nyw1OD
Q3NzM4MzksMTQzNzI5MTY0NSwtMjA4ODc0NjYxMiwzOTA4Mjc2
OTcsLTY0MDY4ODc2NSw0NTQwOTgyOTAsLTEyNDU2MTkxMTQsMT
YyNzg1NDAxNywtMTc5NzcwMjY0OCwtMTY1NDMwMDM1LDc4NjM4
MzQ4NSwtNzMwMzYxMzI3LC0yMDMwNzAyOTI2LDUzODg1Mjk4Ni
wyNzQ1NzEyMDcsMTA4MjkwMzYwOSwxNzAwNTk5NTUwLDE1OTc5
MDY4MF19
-->