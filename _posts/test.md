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
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5NzIwMjY0OCwxNjA2OTM2MDk3LDU4ND
c3MzgzOSwxNDM3MjkxNjQ1LC0yMDg4NzQ2NjEyLDM5MDgyNzY5
NywtNjQwNjg4NzY1LDQ1NDA5ODI5MCwtMTI0NTYxOTExNCwxNj
I3ODU0MDE3LC0xNzk3NzAyNjQ4LC0xNjU0MzAwMzUsNzg2Mzgz
NDg1LC03MzAzNjEzMjcsLTIwMzA3MDI5MjYsNTM4ODUyOTg2LD
I3NDU3MTIwNywxMDgyOTAzNjA5LDE3MDA1OTk1NTAsMTU5Nzkw
NjgwXX0=
-->