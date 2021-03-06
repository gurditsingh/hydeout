## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. **Repartitioning Topic :-**
 
	 In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are **Map, FlatMap and SelectKey** etc. Repartitioning is done automatically take care by kafka streams behind the scenes.


	**Can we avoid the repartition or why do we need repartition ?**
	In kafka stream architecture when we changed the key data needs to be shuffle/repartitioned around the streaming application where data need to written back to kafka and again reads the data back from the new key and grouped the data.
	
 2. **Changelog Topic :-**

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxOTkzMjUwNSwxMTk2MjgzMzE2LDE2Nz
g1ODUxOTUsLTUwMTAxMzI2MSwyMDM2NzcyNDQzLC0yMDg4NzQ2
NjEyLC05NTAwMjUwMTIsLTUwNDI3MzQ3MCwtMTE2MTc0MDU3NS
wtMjE0NjUxMDAwMywyMDgyNjAxNjE2LC0yMTEzNzI5OTMyLC05
MzE2MjE5NSw2Mzk1MzUwMDAsMTYzNjg4OTA1MiwtNjc2MjEzOT
Y2LC0xMDg4MjE0NTU0LC0xMTEzNTYzODI2LC0xOTQ0Njc3NDQw
LDE2NzI4ODM3MzFdfQ==
-->