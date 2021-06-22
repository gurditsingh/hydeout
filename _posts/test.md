
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - Delta Lake facilitates Scheme Evolution which allow to users to easily change the table schema to accommodate the new data with new schema (either add new columns or remove old columns).
 

# Lets first examine the Schema Enforcement

## Schema Enforcement

In Delta Lake the schema enforcement also known as schema validation which in ensure the data quality in delta lake tables. Delta Lake uses schema validation/enforcement on write. When any new data comes first its checked for data compatibility with with the target table schema at the time of writing. If the schema is not matched with the target table Delta Lake reject the transaction and raise the exception schema mismatch.


Schema enforcement, also known as schema validation, is a safeguard in Delta Lake that ensures data quality by rejecting writes to a table that doesn’t match the table’s schema.



![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjAxMDc4NCwtMjAwNDUxNzMyMiwtMT
Y0MzI2MTY0MywtMTkyODAwNzQ4OSw3NDcwNTkwNzksNjcxNTI4
NTE1LC02OTE4MTc4NDQsMTI1NTEwODYsLTMwMjIxMzU2OSwtNj
Y3NTE4NTAzLC0xNjcwMjg1MzcyLDIwOTU5NDc1NzgsMTI2MDAx
MjIyMywxMjUwNTU2ODUwLDYxOTg2MjU5MiwtMTc1NzQyMzQ0Ni
wtMTgxNzIxOTQsMjExNDIxNTU5NCwxMDQ2NjIxNCwtMTMwNTUy
MzU2N119
-->