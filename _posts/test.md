## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (DWU). It ranges from DW100c to DW30000c, higher configuration has more nodes.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.

## How organizations use the SQL Data Warehouse ?

 - If you want to independently size compute power regardless of your storage needs because the compute nodes and the storage nodes are kept separate.
 - This way allows you can grow or shrink the compute power without moving that data. what you're doing is you're moving to compute node over to the data rather than moving all the date around, putting in one place, and then having to analyze it there. You can grow or shrink the compute power.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0MzI1ODkwMCwxMjcxNjE5NzYsMzExNT
MzOTQ2LDM1ODA4ODYzNCwtNjE0Mjk2MDg2LC0yMDg2ODg0Nzky
LDMxODIxMDQ2OCwtOTMyNTQ1MDYzLC0xMDQwMzQ1NzI5LC0yOT
czNzY0MTUsMTExNjAxMjc2OSwtNjE4MTQ3OTk2LC0xOTIwMTQ4
ODQ1LC01MTYzNjQ3ODIsMTg4OTgwNTE0MSwxNTM0OTc4ODQyLD
cxNTE2NDcwMywxNjY2OTYwOTE4LC0yMTAxMDU2NywtNzExNzA4
MzYxXX0=
-->