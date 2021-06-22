
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - Delta Lake facilitates Scheme Evolution which allow to users to easily change the table schema to accommodate the new data with new schema (either add new columns or remove old columns).
 

# Lets first examine the Schema Enforcement

## Schema Enforcement


![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTcwODQwMzcsLTIwMDQ1MTczMjIsLT
E2NDMyNjE2NDMsLTE5MjgwMDc0ODksNzQ3MDU5MDc5LDY3MTUy
ODUxNSwtNjkxODE3ODQ0LDEyNTUxMDg2LC0zMDIyMTM1NjksLT
Y2NzUxODUwMywtMTY3MDI4NTM3MiwyMDk1OTQ3NTc4LDEyNjAw
MTIyMjMsMTI1MDU1Njg1MCw2MTk4NjI1OTIsLTE3NTc0MjM0ND
YsLTE4MTcyMTk0LDIxMTQyMTU1OTQsMTA0NjYyMTQsLTEzMDU1
MjM1NjddfQ==
-->