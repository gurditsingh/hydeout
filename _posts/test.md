## What is KStream
A **KStream** is an abstraction of a **record stream**, where each data record represents in the unbounded data set. Using the table analogy, data records in a record stream are always interpreted as an “INSERT” – because no record replaces an existing row with the same key.

`KStream` can be created directly from one or many Kafka topics (using StreamsBuilder.stream) or as a result of transformations on an existing `KStream`.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4MTMxNjQxLC0xOTI3MjU3ODcwLDE2MT
ExMDQxMDUsLTExNDMxNzYwNjYsMTc1MjMzMDk1NSwtMTM0ODQ4
NDg0OSwtMTkyMjAxMDkxNCw0OTA4NjA2NTYsNzYxOTM4MTcyLC
02MjY0NjAwMDQsMTMwMTMyMjQ0MiwtMTY5Mjc2NzcwLC04NTI4
NjE3NDcsMTMyMjYyMTMzMCwxMzYwNDM0MjUsMTAxNTgxMzUzNC
wtMjA4ODc0NjYxMiwyMDU2NzA2MTA1LDE5NjY4MTM1NzgsLTYw
OTA3NDI1OF19
-->