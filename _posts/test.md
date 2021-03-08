## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka topic).
 

> The **maximum parallelism** at which your application may run is bounded by the maximum number of stream tasks, which itself is determined by maximum number of partitions of the input topic(s) the application is reading from. For example, if your input topic has 5 partitions, then you can run up to 5 applications instances. These instances will collaboratively process the topic’s data. If you run a larger number of app instances than partitions of the input topic, the “excess” app instances will launch but remain idle.



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAxNTgxMzUzNCwyMDU2NzA2MTA1LDE5Nj
Y4MTM1NzgsLTYwOTA3NDI1OCw3OTc4ODg1MTUsOTM5NDkxNTkz
LC02Mjk2MDgyMTUsMTcxMzcxNDA0NCwxNjcxMDAxMzQyLDEzMT
k5MzI1MDUsMTE5NjI4MzMxNiwxNjc4NTg1MTk1LC01MDEwMTMy
NjEsMjAzNjc3MjQ0MywtMjA4ODc0NjYxMiwtOTUwMDI1MDEyLC
01MDQyNzM0NzAsLTExNjE3NDA1NzUsLTIxNDY1MTAwMDMsMjA4
MjYwMTYxNl19
-->