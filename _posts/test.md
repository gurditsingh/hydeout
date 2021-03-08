## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology and then  scaled it by breaking it into multiple stream tasks.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzMjAyOTMyLC0yMDg4NzQ2NjEyLDIwNT
Y3MDYxMDUsMTk2NjgxMzU3OCwtNjA5MDc0MjU4LDc5Nzg4ODUx
NSw5Mzk0OTE1OTMsLTYyOTYwODIxNSwxNzEzNzE0MDQ0LDE2Nz
EwMDEzNDIsMTMxOTkzMjUwNSwxMTk2MjgzMzE2LDE2Nzg1ODUx
OTUsLTUwMTAxMzI2MSwyMDM2NzcyNDQzLC05NTAwMjUwMTIsLT
UwNDI3MzQ3MCwtMTE2MTc0MDU3NSwtMjE0NjUxMDAwMywyMDgy
NjAxNjE2XX0=
-->