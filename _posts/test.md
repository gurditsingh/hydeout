
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure only matched data to be write and reject all the mista
This allows for a few neat capabilities and features such as schema validation, to ensure quality data by rejecting writes to a table that do not match the table's schema
![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzQzODU2NjQsLTE2NDMyNjE2NDMsLT
E5MjgwMDc0ODksNzQ3MDU5MDc5LDY3MTUyODUxNSwtNjkxODE3
ODQ0LDEyNTUxMDg2LC0zMDIyMTM1NjksLTY2NzUxODUwMywtMT
Y3MDI4NTM3MiwyMDk1OTQ3NTc4LDEyNjAwMTIyMjMsMTI1MDU1
Njg1MCw2MTk4NjI1OTIsLTE3NTc0MjM0NDYsLTE4MTcyMTk0LD
IxMTQyMTU1OTQsMTA0NjYyMTQsLTEzMDU1MjM1NjcsLTE0NTk5
Mjc1NzVdfQ==
-->