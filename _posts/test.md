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


## Massive Parallel Processing
```
[ ![](small.jpg) ](large.jpg)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3OTA5MDMyNjEsMTcwMDU5OTU1MCwxMj
cxNjE5NzYsMzExNTMzOTQ2LDM1ODA4ODYzNCwtNjE0Mjk2MDg2
LC0yMDg2ODg0NzkyLDMxODIxMDQ2OCwtOTMyNTQ1MDYzLC0xMD
QwMzQ1NzI5LC0yOTczNzY0MTUsMTExNjAxMjc2OSwtNjE4MTQ3
OTk2LC0xOTIwMTQ4ODQ1LC01MTYzNjQ3ODIsMTg4OTgwNTE0MS
wxNTM0OTc4ODQyLDcxNTE2NDcwMywxNjY2OTYwOTE4LC0yMTAx
MDU2N119
-->