## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (DWU). It ranges from DW100c to DW30000c, higher configuration has more nodes.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.

Some important 

![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/synapse-unifid-platform.png?raw=true)


## Next ?

Planning to create multiple blogs episodes on azure synapse covering various areas related to azure synapse and showing you the way of using these services for implementing your data warehouse solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU4MDg4NjM0LC02MTQyOTYwODYsLTIwOD
Y4ODQ3OTIsMzE4MjEwNDY4LC05MzI1NDUwNjMsLTEwNDAzNDU3
MjksLTI5NzM3NjQxNSwxMTE2MDEyNzY5LC02MTgxNDc5OTYsLT
E5MjAxNDg4NDUsLTUxNjM2NDc4MiwxODg5ODA1MTQxLDE1MzQ5
Nzg4NDIsNzE1MTY0NzAzLDE2NjY5NjA5MTgsLTIxMDEwNTY3LC
03MTE3MDgzNjEsLTM5NjcxNzI4Niw2ODU1MzA3OTEsNzE1MzAy
NzUyXX0=
-->