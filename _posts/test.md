## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka topic).
 

> The **maximum parallelism** at which your application may run is bounded by the maximum number of stream tasks, which itself is determined by maximum number of partitions of the input topic(s) the application is reading from. For example, if your input topic has 5 partitions, then you can run up to 5 applications instances. These instances will collaboratively process the topic’s data. If you run a larger number of app instances than partitions of the input topic, the “excess” app instances will launch but remain idle.

##  Breaking your topology down into sub-topologies and creates tasks



<!--stackedit_data:
eyJoaXN0b3J5IjpbMzI4NjMwODM3LDEwMTU4MTM1MzQsLTIwOD
g3NDY2MTIsMjA1NjcwNjEwNSwxOTY2ODEzNTc4LC02MDkwNzQy
NTgsNzk3ODg4NTE1LDkzOTQ5MTU5MywtNjI5NjA4MjE1LDE3MT
M3MTQwNDQsMTY3MTAwMTM0MiwxMzE5OTMyNTA1LDExOTYyODMz
MTYsMTY3ODU4NTE5NSwtNTAxMDEzMjYxLDIwMzY3NzI0NDMsLT
k1MDAyNTAxMiwtNTA0MjczNDcwLC0xMTYxNzQwNTc1LC0yMTQ2
NTEwMDAzXX0=
-->