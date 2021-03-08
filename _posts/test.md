## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcxOTAyNDIxNywyMDU2NzA2MTA1LDE5Nj
Y4MTM1NzgsLTYwOTA3NDI1OCw3OTc4ODg1MTUsOTM5NDkxNTkz
LC02Mjk2MDgyMTUsMTcxMzcxNDA0NCwxNjcxMDAxMzQyLDEzMT
k5MzI1MDUsMTE5NjI4MzMxNiwxNjc4NTg1MTk1LC01MDEwMTMy
NjEsMjAzNjc3MjQ0MywtMjA4ODc0NjYxMiwtOTUwMDI1MDEyLC
01MDQyNzM0NzAsLTExNjE3NDA1NzUsLTIxNDY1MTAwMDMsMjA4
MjYwMTYxNl19
-->