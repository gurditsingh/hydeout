## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg3NDU2OTM0MywtMjA4ODc0NjYxMiwyMD
U2NzA2MTA1LDE5NjY4MTM1NzgsLTYwOTA3NDI1OCw3OTc4ODg1
MTUsOTM5NDkxNTkzLC02Mjk2MDgyMTUsMTcxMzcxNDA0NCwxNj
cxMDAxMzQyLDEzMTk5MzI1MDUsMTE5NjI4MzMxNiwxNjc4NTg1
MTk1LC01MDEwMTMyNjEsMjAzNjc3MjQ0MywtOTUwMDI1MDEyLC
01MDQyNzM0NzAsLTExNjE3NDA1NzUsLTIxNDY1MTAwMDMsMjA4
MjYwMTYxNl19
-->