## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta Lakes that allow data practitioners to go back in time and solve for these challenges. It is uncertain if time travel to the past is physically possible but data practitioners can time travel programmatically with Delta Lake. Delta Lake allows automatic versioning of all data stored in the data lake and we can time travel to any version. It also allows us to create a copy of an existing Delta table at a specific version using the clone command to help with a few time travel use cases. To under‐ stand these functionalities and how time travel works, we first need to unpack the file structure of Delta tables and deep dive into each of the components.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTc4MzE2NjksLTEyMTU2OTQyMTMsLT
E0MzExMDMyODIsLTE3MjA0MzAzOTIsLTIwODg3NDY2MTIsLTE1
NzQ2Mjg2MjEsLTc2NjQ1MDE2NCw4NjU1Njc2NjIsNTIzMjEyNz
Q3LC0xODAwNTI3MjkyLC0xMjkwNDIwOTc2LC0xODgxMzU4MDM3
LDg1NzA5OTIyMCwtMTg0MDkxMjY1OCwxMzkwMjczNDA3LC0xND
kwNzY0NDc1LC00NDQ4NzU1ODMsMTA0NDM1NzU4OSwtMTk5NTU5
MTYyMSwxNzk3MjQ3OTE2XX0=
-->