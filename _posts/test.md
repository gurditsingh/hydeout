## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. **Repartitioning Topic :-**
 
	 In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are **Map, FlatMap and SelectKey** etc. 
 
	 Repartitioning is done automatically take care by kafka streams behind the scenes.
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTY0MDUzMzYsMTE5NjI4MzMxNiwxNj
c4NTg1MTk1LC01MDEwMTMyNjEsMjAzNjc3MjQ0MywtMjA4ODc0
NjYxMiwtOTUwMDI1MDEyLC01MDQyNzM0NzAsLTExNjE3NDA1Nz
UsLTIxNDY1MTAwMDMsMjA4MjYwMTYxNiwtMjExMzcyOTkzMiwt
OTMxNjIxOTUsNjM5NTM1MDAwLDE2MzY4ODkwNTIsLTY3NjIxMz
k2NiwtMTA4ODIxNDU1NCwtMTExMzU2MzgyNiwtMTk0NDY3NzQ0
MCwxNjcyODgzNzMxXX0=
-->