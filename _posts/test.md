## What is Synapse SQL pool?
Synapse SQL Pool (formerly SQL Data Warehouse) is an MPP Enterprise Data Warehouse on Azure.

-  Synapse SQL pool stores data in relational tables with columnar storage.
-  Synapse SQL pool has compute separate from storage which enables to scale.
-  Synapse Service Level Objective (Compute) is the scalability setting which determines cost and performance of the data warehouse (SQL Pool). It ranges from DW100c to DW30000c, higher configuration has more nodes. The compute is discussed in details in further sections.
-  Workload management is additional feature around managing resource utilization, concurrency and query priority.
-  Synapse compute can be scale up down via SQL, PowerShell and Portal. The SQL ability for scaling is unique, and can be achieved via an “ALTER” command.



![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/synapse-unifid-platform.png?raw=true)
 - **Synapse SQL Pools :** This feature of the service available in a provisioned manner where a fixed capacity of DWU units is allocated to the instance of the service for data processing. Data can be imported into Synapse using different mechanisms like SSIS, Polybase, Azure Data Factory, etc.

	Synapse SQL feature is also available in a serverless manner, where no fixed capacity of the infrastructure needs to be provisioned. Instead, Azure manages the required infrastructure capacity to meet the needs of the workloads.


## Next ?

Planning to create multiple blogs episodes on azure synapse covering various areas related to azure synapse and showing you the way of using these services for implementing your data warehouse solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTc2OTcyMzU2LC0yMDg2ODg0NzkyLDMxOD
IxMDQ2OCwtOTMyNTQ1MDYzLC0xMDQwMzQ1NzI5LC0yOTczNzY0
MTUsMTExNjAxMjc2OSwtNjE4MTQ3OTk2LC0xOTIwMTQ4ODQ1LC
01MTYzNjQ3ODIsMTg4OTgwNTE0MSwxNTM0OTc4ODQyLDcxNTE2
NDcwMywxNjY2OTYwOTE4LC0yMTAxMDU2NywtNzExNzA4MzYxLC
0zOTY3MTcyODYsNjg1NTMwNzkxLDcxNTMwMjc1MiwxODc0Nzkx
MzQyXX0=
-->