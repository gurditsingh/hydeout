## What is Spark Performance Tuning?
Spark Performance Tuning refers to the process of adjusting settings to record for memory, cores, and instances used by the system. This process guarantees that the Spark has a flawless performance and also prevents bottlenecking of resources in Spark.
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-tuning.jpg?raw=true)

 - **Data serialization** also determines a good network performance. You will be able to obtain good results in Spark performance by serialization. Spark supports two serialization libraries Java Serialization, Kryo Serialization.
 - **Memory Tuning** is necessary or important step in tuning. we need to give as much memory so that the entire dataset has to fit in memory.
 -  **Data Structure Tuning** One option to reduce memory consumption is by staying away from java features. Avoid the nested structure with lots of small objects and pointers. Instead of using strings for keys use numeric.
 -  **Garbage Collection Tuning** 
 -  **Memory Management** An efficient memory use is essential to good performance. Spark uses memory mainly for storage and execution. Storage memory is used to cache data that will be reused later. On the other hand, execution memory is used for computation in shuffles, sorts, joins, and aggregations.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE3ODIwNjMyMyw1ODQ3NzM4MzksMTQzNz
I5MTY0NSwtMjA4ODc0NjYxMiwzOTA4Mjc2OTcsLTY0MDY4ODc2
NSw0NTQwOTgyOTAsLTEyNDU2MTkxMTQsMTYyNzg1NDAxNywtMT
c5NzcwMjY0OCwtMTY1NDMwMDM1LDc4NjM4MzQ4NSwtNzMwMzYx
MzI3LC0yMDMwNzAyOTI2LDUzODg1Mjk4NiwyNzQ1NzEyMDcsMT
A4MjkwMzYwOSwxNzAwNTk5NTUwLDE1OTc5MDY4MCwxMjcxNjE5
NzZdfQ==
-->