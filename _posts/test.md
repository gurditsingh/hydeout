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
In the Massive Parallel Processing at the top here we have the control node and this is the application or user connection. The control node is the brain/heart of your massive parallel processing engine. 

It divides it up into 60 different nodes, and what this allows you to do processing in parallel to different nodes that you have of your storage. So what this is going to do is make a very powerful engine to run massive queries upon your data.

It's also broken into different partitions that allow you to just look at and analyze separate pieces of your data as it is going along. Hence the name Massive Parallel Processing. 

And at the bottom we have the Azure storage, this is where you keep your data, and it is separate from the compute power and save most of the cost.

[ ![](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sql-architecture-mpp.png?raw=true) ](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sql-architecture-mpp.png?raw=true)


**Dedicated SQL Pool** uses a node-based architecture. Applications connect and issue T-SQL commands to a Control node. The Control node hosts the distributed query engine, which optimizes queries for parallel processing, and then passes operations to Compute nodes to do their work in parallel. The Compute nodes store all user data in Azure Storage and run the parallel queries.

**Serverless SQL Pool** Control node utilizes Distributed Query Processing (DQP) engine to distributed execution of user query by splitting it into smaller queries that will be executed on Compute nodes. Each small query is called task and represents distributed execution unit. It reads file(s) from storage, joins results from other tasks, groups, or orders data retrieved from other tasks. The Compute nodes store all user data in Azure Storage and run the parallel queries.

**Control node**  This is the front end that interacts with all applications and connections, and the MPP engine runs on the control node, and this optimizes and coordinates your parallel queries. When you submit a T-SQL query, the Control node transforms it into queries that run against each distribution in parallel.

**Compute nodes** provides a computational power for your analytics. It's separated from the storage nodes, and you can scale this using what's called Data Warehouse Units. As you pay for more compute resources, distributions are remapped to available Compute nodes. The number of compute nodes ranges from 1 to 60, and is determined by the service level for Synapse SQL.

**Data Warehouse Units** is a collection of analytic resources that are provisioned, and it's basically a combination of CPU, memory and IO. And you can scale this up and you can scale this down depending upon what your needs are. A DWU, or Data Warehouse Unit, is the basic unit of these different resources, and you can add DWUs or subtracted DWUs.

**Data Movement Service** is the data transport technology that coordinates data movement between the Compute nodes. Some queries require data movement to ensure the parallel queries return accurate results. When data movement is required, DMS ensures the right data gets to the right location.

**Storage Node (Azure Storage)** and lastly, we have the storage node, and the storage node is kept separate from compute in order to keep data at rest. And this data at rest is cheaper than the data that is being analysed.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNTcxOTE1NjQsMTA4MjkwMzYwOSwxNz
AwNTk5NTUwLDE1OTc5MDY4MCwxMjcxNjE5NzYsMzExNTMzOTQ2
LDM1ODA4ODYzNCwtNjE0Mjk2MDg2LC0yMDg2ODg0NzkyLDMxOD
IxMDQ2OCwtOTMyNTQ1MDYzLC0xMDQwMzQ1NzI5LC0yOTczNzY0
MTUsMTExNjAxMjc2OSwtNjE4MTQ3OTk2LC0xOTIwMTQ4ODQ1LC
01MTYzNjQ3ODIsMTg4OTgwNTE0MSwxNTM0OTc4ODQyLDcxNTE2
NDcwM119
-->