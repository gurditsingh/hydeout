## Kafka Streams Partitions and Tasks
The messaging layer of Kafka partitions data for storing and transporting it. Kafka Streams partitions data for  _processing_  it. In both cases, this partitioning is what enables data locality, elasticity, scalability, high performance, and fault tolerance.

Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjg3NzU0MDg1LDIwNTY3MDYxMDUsMTk2Nj
gxMzU3OCwtNjA5MDc0MjU4LDc5Nzg4ODUxNSw5Mzk0OTE1OTMs
LTYyOTYwODIxNSwxNzEzNzE0MDQ0LDE2NzEwMDEzNDIsMTMxOT
kzMjUwNSwxMTk2MjgzMzE2LDE2Nzg1ODUxOTUsLTUwMTAxMzI2
MSwyMDM2NzcyNDQzLC0yMDg4NzQ2NjEyLC05NTAwMjUwMTIsLT
UwNDI3MzQ3MCwtMTE2MTc0MDU3NSwtMjE0NjUxMDAwMywyMDgy
NjAxNjE2XX0=
-->