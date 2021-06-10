
## What is Transaction Log or Delta Log?

The Delta Lake transaction log (also known as the Delta Log) is an ordered record of every change that has been performed on a Delta Lake table.

 - Delta Lake is built on top of Apache Spark so that at the same time multiple readers and writers work on the table.
 - It shows the correct view of the table all times, means due to transaction log feature table will always in updated state.
 - The Delta Lake transaction log serves the single source of truth like a central repository that tracks all changes that users make to the table.
 - No partial or corrupted files because delta lake either the commit the state or abort the state. which means if job fails in between there will be no entry in the transaction log.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NjQxNTg5NzgsMTkxMzQ0NzczMCwxOT
A2NDI5MzA2LC0yNjQ0NzY4MjAsMjcwODQwNjg2LC0yMDU2NzQz
Mjc4LC0zMjE4NTc4NTksLTE1NDgxOTEwNDYsLTYwNjI2Mzk5LD
IxMTU0MzI3MzAsNjg1NjE1Mjk1LC03OTg1NDQ3MzgsMTUwMjQy
Nzk2MywxNTMzODcxMjg5LDYxOTYxNDkyMyw3OTE2MzU3NTgsLT
EwMjkzNjIxMzcsLTM1NjYxOTIwOCwtMjI0NjQ0OTE4LDE5OTEy
MDUxNDddfQ==
-->