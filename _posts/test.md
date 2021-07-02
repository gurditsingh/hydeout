## Problem
Data engineering pipeline often go wrong when dirty/bad data ingested from the external sources. After that it is hard to undo the changes or updates in the data lake. In addition to that there are aspects like data auditing and understand how the data is changed over the time.

## Solution

Delta lake cater the problem and provide a solution to go back in time and solve the above challenges. Delta automatically versions the big data that you store in your data lake. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. Delta lake provide a data managment like functionnality 

This temporal data management simplifies your data pipeline by making it easy to audit, roll back data in case of accidental bad writes or deletes, and reproduce experiments and reports. When we write our data into a Delta table, every operation is automatically versioned and we can access any version of data. 

Delta Lakes that allow data practitioners to go back in time and solve for these challenges. It is uncertain if time travel to the past is physically possible but data practitioners can time travel programmatically with Delta Lake. Delta Lake allows automatic versioning of all data stored in the data lake and we can time travel to any version. It also allows us to create a copy of an existing Delta table at a specific version using the clone command to help with a few time travel use cases. To under‐ stand these functionalities and how time travel works, we first need to unpack the file structure of Delta tables and deep dive into each of the components.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNDk1Mjk2MywtMTU1NzgzMTY2OSwtMT
IxNTY5NDIxMywtMTQzMTEwMzI4MiwtMTcyMDQzMDM5MiwtMjA4
ODc0NjYxMiwtMTU3NDYyODYyMSwtNzY2NDUwMTY0LDg2NTU2Nz
Y2Miw1MjMyMTI3NDcsLTE4MDA1MjcyOTIsLTEyOTA0MjA5NzYs
LTE4ODEzNTgwMzcsODU3MDk5MjIwLC0xODQwOTEyNjU4LDEzOT
AyNzM0MDcsLTE0OTA3NjQ0NzUsLTQ0NDg3NTU4MywxMDQ0MzU3
NTg5LC0xOTk1NTkxNjIxXX0=
-->