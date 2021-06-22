
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - 
which allows users to easily change a table's current schema to accommodate data that is may be changing over time.
![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE3MDg2ODkzLC0xNjQzMjYxNjQzLC0xOT
I4MDA3NDg5LDc0NzA1OTA3OSw2NzE1Mjg1MTUsLTY5MTgxNzg0
NCwxMjU1MTA4NiwtMzAyMjEzNTY5LC02Njc1MTg1MDMsLTE2Nz
AyODUzNzIsMjA5NTk0NzU3OCwxMjYwMDEyMjIzLDEyNTA1NTY4
NTAsNjE5ODYyNTkyLC0xNzU3NDIzNDQ2LC0xODE3MjE5NCwyMT
E0MjE1NTk0LDEwNDY2MjE0LC0xMzA1NTIzNTY3LC0xNDU5OTI3
NTc1XX0=
-->