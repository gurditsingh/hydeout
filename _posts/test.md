## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka topic).
 

> The **maximum parallelism** at which your application may run is bounded by the maximum number of stream tasks, which itself is determined by maximum number of partitions of the input topic(s) the application is reading from. For example, if your input topic has 5 partitions, then you can run up to 5 applications instances. These instances will collaboratively process the topic’s data. If you run a larger number of app instances than partitions of the input topic, the “excess” app instances will launch but remain idle.

##  Breaking your topology down into sub-topologies and creates tasks



<!--stackedit_data:
eyJoaXN0b3J5IjpbMzI4NjMwODM3LDEwMTU4MTM1MzQsMjA1Nj
cwNjEwNSwxOTY2ODEzNTc4LC02MDkwNzQyNTgsNzk3ODg4NTE1
LDkzOTQ5MTU5MywtNjI5NjA4MjE1LDE3MTM3MTQwNDQsMTY3MT
AwMTM0MiwxMzE5OTMyNTA1LDExOTYyODMzMTYsMTY3ODU4NTE5
NSwtNTAxMDEzMjYxLDIwMzY3NzI0NDMsLTIwODg3NDY2MTIsLT
k1MDAyNTAxMiwtNTA0MjczNDcwLC0xMTYxNzQwNTc1LC0yMTQ2
NTEwMDAzXX0=
-->