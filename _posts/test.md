## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake provide 
Delta automatically versions the big data that you store in your data lake, and you can access any historical version of that data. This temporal data management simplifies your data pipeline by making it easy to audit, roll back data in case of accidental bad writes or deletes, and reproduce experiments and reports.

Delta Lakes that allow data practitioners to go back in time and solve for these challenges. It is uncertain if time travel to the past is physically possible but data practitioners can time travel programmatically with Delta Lake. Delta Lake allows automatic versioning of all data stored in the data lake and we can time travel to any version. It also allows us to create a copy of an existing Delta table at a specific version using the clone command to help with a few time travel use cases. To under‐ stand these functionalities and how time travel works, we first need to unpack the file structure of Delta tables and deep dive into each of the components.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzczMTc3MjU2LC0xNTU3ODMxNjY5LC0xMj
E1Njk0MjEzLC0xNDMxMTAzMjgyLC0xNzIwNDMwMzkyLC0yMDg4
NzQ2NjEyLC0xNTc0NjI4NjIxLC03NjY0NTAxNjQsODY1NTY3Nj
YyLDUyMzIxMjc0NywtMTgwMDUyNzI5MiwtMTI5MDQyMDk3Niwt
MTg4MTM1ODAzNyw4NTcwOTkyMjAsLTE4NDA5MTI2NTgsMTM5MD
I3MzQwNywtMTQ5MDc2NDQ3NSwtNDQ0ODc1NTgzLDEwNDQzNTc1
ODksLTE5OTU1OTE2MjFdfQ==
-->