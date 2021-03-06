## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. **Repartitioning Topic :-**
 
	 In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are **Map, FlatMap and SelectKey** etc. Repartitioning is done automatically take care by kafka streams behind the scenes.


	**Can we avoid the repartition or why do we need repartition ?**
	In kafka stream architecture when we changed the key data needs to be shuffle/repartitioned around the streaming application where data need to written back to kafka and again reads the data back from the new key and grouped the data.
	
	
 2. **Changelog Topic :-**
 
	 In case of your streaming application if you start aggregation then kafka stream save aggregated data into changelog topic which is created by kafka streams internally.
 
	 Actually the result of aggregation call creates a state store and for fault-tolerance the state store is backed up by a Kafka Changelog topic. The aggregation results are stored into this internal topic. State will be recovered from changelog topic when applications is restarted and application-id wasn't changed.

	

> Kafka Streams allows for stateful stream processing, i.e. operators that have an internal state. This internal state is managed in so-called state stores. A state store can be ephemeral (lost on failure) or fault-tolerant (restored after the failure). The default implementation used by Kafka Streams DSL is a fault-tolerant state store using 1. an internally created and compacted changelog topic (for fault-tolerance) and 2. one (or multiple) RocksDB instances (for  cached key-value lookups). Thus, in case of starting/stopping  applications and rewinding/reprocessing, this internal data needs to get managed correctly.


## Lets see in example 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjA5MzA0NjksMTMxOTkzMjUwNSwxMT
k2MjgzMzE2LDE2Nzg1ODUxOTUsLTUwMTAxMzI2MSwyMDM2Nzcy
NDQzLC0yMDg4NzQ2NjEyLC05NTAwMjUwMTIsLTUwNDI3MzQ3MC
wtMTE2MTc0MDU3NSwtMjE0NjUxMDAwMywyMDgyNjAxNjE2LC0y
MTEzNzI5OTMyLC05MzE2MjE5NSw2Mzk1MzUwMDAsMTYzNjg4OT
A1MiwtNjc2MjEzOTY2LC0xMDg4MjE0NTU0LC0xMTEzNTYzODI2
LC0xOTQ0Njc3NDQwXX0=
-->