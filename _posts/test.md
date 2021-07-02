## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. Delta lake provide a data management like functionality in which you do easy audit, roll back of bad data and reproduce the data.


<!--stackedit_data:
eyJoaXN0b3J5IjpbODUxMzU3MTAyLC0xNTU3ODMxNjY5LC0xMj
E1Njk0MjEzLC0xNDMxMTAzMjgyLC0xNzIwNDMwMzkyLC0yMDg4
NzQ2NjEyLC0xNTc0NjI4NjIxLC03NjY0NTAxNjQsODY1NTY3Nj
YyLDUyMzIxMjc0NywtMTgwMDUyNzI5MiwtMTI5MDQyMDk3Niwt
MTg4MTM1ODAzNyw4NTcwOTkyMjAsLTE4NDA5MTI2NTgsMTM5MD
I3MzQwNywtMTQ5MDc2NDQ3NSwtNDQ0ODc1NTgzLDEwNDQzNTc1
ODksLTE5OTU1OTE2MjFdfQ==
-->