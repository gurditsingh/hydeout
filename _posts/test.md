## What are internal topics used in Kafka Streams?
when we create any streaming application kafka internally creates few topics to manage the state and other aspects of streaming.

 1. Repartitioning Topic :- In case of your streaming application if you start transforming the key of your stream, a repartition will happen and create internal topic for repartitioning.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3ODU4NTE5NSwtNTAxMDEzMjYxLDIwMz
Y3NzI0NDMsLTIwODg3NDY2MTIsLTk1MDAyNTAxMiwtNTA0Mjcz
NDcwLC0xMTYxNzQwNTc1LC0yMTQ2NTEwMDAzLDIwODI2MDE2MT
YsLTIxMTM3Mjk5MzIsLTkzMTYyMTk1LDYzOTUzNTAwMCwxNjM2
ODg5MDUyLC02NzYyMTM5NjYsLTEwODgyMTQ1NTQsLTExMTM1Nj
M4MjYsLTE5NDQ2Nzc0NDAsMTY3Mjg4MzczMSwtNzQ1NTg0NzEz
LC02NDcyOTk2NzhdfQ==
-->