
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like Schema Enforcement and Scheme Evolution.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - Delta Lake facilitates Scheme Evolution which allow to users to easily change the table schema to accommodate the new data with new schema (either add new column).
![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4MjA2Mjk5NiwtMTY0MzI2MTY0MywtMT
kyODAwNzQ4OSw3NDcwNTkwNzksNjcxNTI4NTE1LC02OTE4MTc4
NDQsMTI1NTEwODYsLTMwMjIxMzU2OSwtNjY3NTE4NTAzLC0xNj
cwMjg1MzcyLDIwOTU5NDc1NzgsMTI2MDAxMjIyMywxMjUwNTU2
ODUwLDYxOTg2MjU5MiwtMTc1NzQyMzQ0NiwtMTgxNzIxOTQsMj
ExNDIxNTU5NCwxMDQ2NjIxNCwtMTMwNTUyMzU2NywtMTQ1OTky
NzU3NV19
-->