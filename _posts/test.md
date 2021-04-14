## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

Executor Cores/Slots : 


![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4NDgzNTQ4NywtMTQxNDgwODY4NiwtNz
M2NDkwMjMzLC0xNzg2NjM3MjI5LDMyOTU4ODM1NiwyMDQ3NjU0
NDQsLTU4NTQyMzY4MCwyODI5NjQ4OTAsLTEzMDY2MzUyNTgsLT
UxNzA3MDYyNSwtMTg1MjY1NDEwOSwtMTc4MTUyMzA1Miw4MTk0
MTY1NDYsLTEyMTM3NzkzMDQsLTExNzc4OTgyMDAsLTE1OTI3Nz
Y4MzksLTEzMzQyNzM1NTAsLTYwMTIzMjgwNCwtOTYwMjcyMDE2
LDU1MjkyNTAxM119
-->