## High Level Spark Hierarchy

A Spark application consists of a single driver process and a set of executor processes scattered across nodes on the cluster. The driver is the process that is in charge of the high-level control flow of work that needs to be done. The executor processes are responsible for executing this work, in the form of  _tasks_, as well as for storing any data that the user chooses to cache. Both the driver and the executors typically stick around for the entire time the application is running.

Executor Cores/Slots : slots indicate threads available to perform parallel work for Spark. Spark documentation often refers to these threads as cores, which is a confusing term, as the number of slots available on a particular machine does not necessarily have any relationship to the number of physical CPU cores on that machine.


![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_hierarchy.png?raw=true)



## Next ?

Planning to create multiple blogs episodes on Spark Performance Tuning. Understand and covering the various areas of spark where we can improve the pipeline/job.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTg4NjE1MDkzLDIwODQ4MzU0ODcsLTE0MT
Q4MDg2ODYsLTczNjQ5MDIzMywtMTc4NjYzNzIyOSwzMjk1ODgz
NTYsMjA0NzY1NDQ0LC01ODU0MjM2ODAsMjgyOTY0ODkwLC0xMz
A2NjM1MjU4LC01MTcwNzA2MjUsLTE4NTI2NTQxMDksLTE3ODE1
MjMwNTIsODE5NDE2NTQ2LC0xMjEzNzc5MzA0LC0xMTc3ODk4Mj
AwLC0xNTkyNzc2ODM5LC0xMzM0MjczNTUwLC02MDEyMzI4MDQs
LTk2MDI3MjAxNl19
-->