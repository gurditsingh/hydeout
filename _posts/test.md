## Kafka Streams Partitions and Tasks
Kafka Streams uses the concepts of  **stream partitions**  and  **stream tasks**  as logical units of its parallelism model. There are close links between Kafka Streams and Kafka in the context of parallelism:

 - First Kafka stream analyse the applications processor or topology (user defined kafka stream application) and then scaled it by breaking it into multiple stream tasks.
 - Next Kafka Streams creates a fixed number of stream tasks based on the input stream partitions for the application.
 - Next each task being assigned a list of partitions from the input streams (kafka topic).
 

> The **maximum parallelism** at which your application may run is bounded by the maximum number of stream tasks, which itself is determined by maximum number of partitions of the input topic(s) the application is reading from. For example, if your input topic has 5 partitions, then you can run up to 5 applications instances. These instances will collaboratively process the topic’s data. If you run a larger number of app instances than partitions of the input topic, the “excess” app instances will launch but remain idle.

##  Breaking your topology down into sub-topologies and creates tasks
Let's understand by one simple example mentioned below. 

```scala
    streamBuilder
            .mapValues(value -> value.toLowerCase())
            .flatMapValues(value -> Arrays.asList(value.split("#")))
            .selectKey((key, value) -> value)
            .groupByKey()
            .count()
            .toStream()
            .to("out_word");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMyMjYyMTMzMCwxMzYwNDM0MjUsMTAxNT
gxMzUzNCwyMDU2NzA2MTA1LDE5NjY4MTM1NzgsLTYwOTA3NDI1
OCw3OTc4ODg1MTUsOTM5NDkxNTkzLC02Mjk2MDgyMTUsMTcxMz
cxNDA0NCwxNjcxMDAxMzQyLDEzMTk5MzI1MDUsMTE5NjI4MzMx
NiwxNjc4NTg1MTk1LC01MDEwMTMyNjEsMjAzNjc3MjQ0MywtMj
A4ODc0NjYxMiwtOTUwMDI1MDEyLC01MDQyNzM0NzAsLTExNjE3
NDA1NzVdfQ==
-->