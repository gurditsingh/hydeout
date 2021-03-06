## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. Repartitioning Topic :- In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning. The operation which can possibly change the key are Map, FlatMap and SelectKey etc. 
 
 Repartitioning is done automatically take care by kafka streams behind the scenes.  

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE5NjI4MzMxNiwxNjc4NTg1MTk1LC01MD
EwMTMyNjEsMjAzNjc3MjQ0MywtMjA4ODc0NjYxMiwtOTUwMDI1
MDEyLC01MDQyNzM0NzAsLTExNjE3NDA1NzUsLTIxNDY1MTAwMD
MsMjA4MjYwMTYxNiwtMjExMzcyOTkzMiwtOTMxNjIxOTUsNjM5
NTM1MDAwLDE2MzY4ODkwNTIsLTY3NjIxMzk2NiwtMTA4ODIxND
U1NCwtMTExMzU2MzgyNiwtMTk0NDY3NzQ0MCwxNjcyODgzNzMx
LC03NDU1ODQ3MTNdfQ==
-->