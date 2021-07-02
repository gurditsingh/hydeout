## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. Delta lake provide a data management like functionality in which you do easy audit, roll back of bad data and reproduce the data.

## Lets first create a Delta table

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk2NjUxNjc2OSw4NTEzNTcxMDIsLTE1NT
c4MzE2NjksLTEyMTU2OTQyMTMsLTE0MzExMDMyODIsLTE3MjA0
MzAzOTIsLTIwODg3NDY2MTIsLTE1NzQ2Mjg2MjEsLTc2NjQ1MD
E2NCw4NjU1Njc2NjIsNTIzMjEyNzQ3LC0xODAwNTI3MjkyLC0x
MjkwNDIwOTc2LC0xODgxMzU4MDM3LDg1NzA5OTIyMCwtMTg0MD
kxMjY1OCwxMzkwMjczNDA3LC0xNDkwNzY0NDc1LC00NDQ4NzU1
ODMsMTA0NDM1NzU4OV19
-->