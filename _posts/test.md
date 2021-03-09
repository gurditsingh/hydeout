## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka topic).
 

> The **maximum parallelism** at which your application may run is bounded by the maximum number of stream tasks, which itself is determined by maximum number of partitions of the input topic(s) the application is reading from. For example, if your input topic has 5 partitions, then you can run up to 5 applications instances. These instances will collaboratively process the topic’s data. If you run a larger number of app instances than partitions of the input topic, the “excess” app instances will launch but remain idle.

How Kafka create tasks from Topology



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc1MzMwMTExOSwxMDE1ODEzNTM0LDIwNT
Y3MDYxMDUsMTk2NjgxMzU3OCwtNjA5MDc0MjU4LDc5Nzg4ODUx
NSw5Mzk0OTE1OTMsLTYyOTYwODIxNSwxNzEzNzE0MDQ0LDE2Nz
EwMDEzNDIsMTMxOTkzMjUwNSwxMTk2MjgzMzE2LDE2Nzg1ODUx
OTUsLTUwMTAxMzI2MSwyMDM2NzcyNDQzLC0yMDg4NzQ2NjEyLC
05NTAwMjUwMTIsLTUwNDI3MzQ3MCwtMTE2MTc0MDU3NSwtMjE0
NjUxMDAwM119
-->