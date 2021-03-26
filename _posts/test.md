## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (DWU). It ranges from DW100c to DW30000c, higher configuration has more nodes.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.

## Some important concepts in SQL Pool


![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/synapse-unifid-platform.png?raw=true)


## Next ?

Planning to create multiple blogs episodes on azure synapse covering various areas related to azure synapse and showing you the way of using these services for implementing your data warehouse solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzExNTMzOTQ2LDM1ODA4ODYzNCwtNjE0Mj
k2MDg2LC0yMDg2ODg0NzkyLDMxODIxMDQ2OCwtOTMyNTQ1MDYz
LC0xMDQwMzQ1NzI5LC0yOTczNzY0MTUsMTExNjAxMjc2OSwtNj
E4MTQ3OTk2LC0xOTIwMTQ4ODQ1LC01MTYzNjQ3ODIsMTg4OTgw
NTE0MSwxNTM0OTc4ODQyLDcxNTE2NDcwMywxNjY2OTYwOTE4LC
0yMTAxMDU2NywtNzExNzA4MzYxLC0zOTY3MTcyODYsNjg1NTMw
NzkxXX0=
-->