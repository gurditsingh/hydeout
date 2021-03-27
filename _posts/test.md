## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (DWU). It ranges from DW100c to DW30000c, higher configuration has more nodes.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.

## How organizations use the SQL Data Warehouse ?

 - If you want to independently size compute power regardless of your storage needs because the compute nodes and the storage nodes are kept separate.
 - this allows you to do is grow or shrink the compute power without moving that data, and without moving that data, essentially, what you're doing is you're moving to compute node over to the data rather than moving all the date around, putting in one place, and then having to analyze it there. You can grow or shrink this compute power

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzUyNjcxOTc2LDEyNzE2MTk3NiwzMTE1Mz
M5NDYsMzU4MDg4NjM0LC02MTQyOTYwODYsLTIwODY4ODQ3OTIs
MzE4MjEwNDY4LC05MzI1NDUwNjMsLTEwNDAzNDU3MjksLTI5Nz
M3NjQxNSwxMTE2MDEyNzY5LC02MTgxNDc5OTYsLTE5MjAxNDg4
NDUsLTUxNjM2NDc4MiwxODg5ODA1MTQxLDE1MzQ5Nzg4NDIsNz
E1MTY0NzAzLDE2NjY5NjA5MTgsLTIxMDEwNTY3LC03MTE3MDgz
NjFdfQ==
-->