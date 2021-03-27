## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (DWU). It ranges from DW100c to DW30000c, higher configuration has more nodes.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.

## How organizations use the SQL Data Warehouse ?

 - If you want to independently size compute power regardless of your storage needs because the compute nodes and the storage nodes are kept separate.
 - This way allows you can grow or shrink the compute power without moving that data. what you're doing is you're moving to compute node over to the data rather than moving all the date around, putting in one place, and then having to analyse it there. You can grow or shrink the compute power.
 - You can pause your compute capacity while leaving data intact so this makes it so you only pay for the storage(storage is more cheaper than the processing).
 - You can resume your compute capacity during business hours and start processing the data for reporting and etc.




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMDI1ODEwNzQsMTI3MTYxOTc2LDMxMT
UzMzk0NiwzNTgwODg2MzQsLTYxNDI5NjA4NiwtMjA4Njg4NDc5
MiwzMTgyMTA0NjgsLTkzMjU0NTA2MywtMTA0MDM0NTcyOSwtMj
k3Mzc2NDE1LDExMTYwMTI3NjksLTYxODE0Nzk5NiwtMTkyMDE0
ODg0NSwtNTE2MzY0NzgyLDE4ODk4MDUxNDEsMTUzNDk3ODg0Mi
w3MTUxNjQ3MDMsMTY2Njk2MDkxOCwtMjEwMTA1NjcsLTcxMTcw
ODM2MV19
-->