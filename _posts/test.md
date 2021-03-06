## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

### Repartitioning Topic
	 In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are **Map, FlatMap and SelectKey** etc. 
	 
	Repartitioning is done automatically take care by kafka streams behind the scenes.  

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjY5NzEzMDExLDExOTYyODMzMTYsMTY3OD
U4NTE5NSwtNTAxMDEzMjYxLDIwMzY3NzI0NDMsLTIwODg3NDY2
MTIsLTk1MDAyNTAxMiwtNTA0MjczNDcwLC0xMTYxNzQwNTc1LC
0yMTQ2NTEwMDAzLDIwODI2MDE2MTYsLTIxMTM3Mjk5MzIsLTkz
MTYyMTk1LDYzOTUzNTAwMCwxNjM2ODg5MDUyLC02NzYyMTM5Nj
YsLTEwODgyMTQ1NTQsLTExMTM1NjM4MjYsLTE5NDQ2Nzc0NDAs
MTY3Mjg4MzczMV19
-->