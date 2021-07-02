## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake, and you can access any historical version of that data. 

This temporal data management simplifies your data pipeline by making it easy to audit, roll back data in case of accidental bad writes or deletes, and reproduce experiments and reports. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. 

Delta Lakes that allow data practitioners to go back in time and solve for these challenges. It is uncertain if time travel to the past is physically possible but data practitioners can time travel programmatically with Delta Lake. Delta Lake allows automatic versioning of all data stored in the data lake and we can time travel to any version. It also allows us to create a copy of an existing Delta table at a specific version using the clone command to help with a few time travel use cases. To under‐ stand these functionalities and how time travel works, we first need to unpack the file structure of Delta tables and deep dive into each of the components.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTk5OTU2NjAsLTE1NTc4MzE2NjksLT
EyMTU2OTQyMTMsLTE0MzExMDMyODIsLTE3MjA0MzAzOTIsLTIw
ODg3NDY2MTIsLTE1NzQ2Mjg2MjEsLTc2NjQ1MDE2NCw4NjU1Nj
c2NjIsNTIzMjEyNzQ3LC0xODAwNTI3MjkyLC0xMjkwNDIwOTc2
LC0xODgxMzU4MDM3LDg1NzA5OTIyMCwtMTg0MDkxMjY1OCwxMz
kwMjczNDA3LC0xNDkwNzY0NDc1LC00NDQ4NzU1ODMsMTA0NDM1
NzU4OSwtMTk5NTU5MTYyMV19
-->