## Spark Hierarchy

A Spark application consists of a single  _driver_  process and a set of  _executor_  processes scattered across nodes on the cluster.

The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running



![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE1NjY1MjM3MCwtNzM2NDkwMjMzLC0xNz
g2NjM3MjI5LDMyOTU4ODM1NiwyMDQ3NjU0NDQsLTU4NTQyMzY4
MCwyODI5NjQ4OTAsLTEzMDY2MzUyNTgsLTUxNzA3MDYyNSwtMT
g1MjY1NDEwOSwtMTc4MTUyMzA1Miw4MTk0MTY1NDYsLTEyMTM3
NzkzMDQsLTExNzc4OTgyMDAsLTE1OTI3NzY4MzksLTEzMzQyNz
M1NTAsLTYwMTIzMjgwNCwtOTYwMjcyMDE2LDU1MjkyNTAxMywx
NzMxNDkxODI1XX0=
-->