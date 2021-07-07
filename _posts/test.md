## Problem
Data lakes hold large amount of data, and needs to perform updates, merge and delete operation on data at all times. With the traditional data lakes it difficult to perform such a simple operations. So that the user need to build there own strategy to perform these operations but in this approach data consistency is big threat, and it can become 

Data lakes can hold a tremendous amount of data, and companies need ways to reliably perform update, merge and delete operations on that data so that it can remain up to date at all times. With traditional data lakes, it can be incredibly difficult to perform simple operations like these, and to confirm that they occurred successfully, because there is no mechanism to ensure data consistency. Without such a mechanism, it becomes difficult for data scientists to reason about their data.


## What is DML Operation

DML refers to "Data Manipulation Language", a subset of SQL statements which deals with data manipulation. A transaction is a sequence of one or more SQL statements that can SELECT, INSERT, UPDATE, DELETE the data.



















![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep5_t7.JPG?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjc1NjQwNjksMjgwMDczMzMxLDU1NDI0OT
A1MiwtMTExNDg0Njg4NSw1NzM3Mzg0ODksLTQwNDkwMzI0MSwx
NjQzMzE2NTEsLTEzODcxOTc5OTMsMTU4NzI5OTkwMiwtNzU5Mj
MxNzc4LDk2MTE1ODY3NCwtMTczNTI3MjcyMywtMTQxMjIxNjEw
LDExMTg3MzQ5MSwxOTY2NTE2NzY5LDg1MTM1NzEwMiwtMTU1Nz
gzMTY2OSwtMTIxNTY5NDIxMywtMTQzMTEwMzI4MiwtMTcyMDQz
MDM5Ml19
-->