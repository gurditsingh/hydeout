# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate a monotonically increasing and unique, but not consecutive. However the numbers won’t be consecutive if the dataframe has more than 1 partition. Let’s see a simple example to understand it

 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTk4NTUxMTAwLDM2MzA0OTI5NSwtMjEyMj
Q1ODEwMiwtOTA5Nzc0MzEwLDExNDc2NTQ4MywtNTU4OTA4MDc3
LC0xMDQ4NDc1OTQ1LC0yMDg4NzQ2NjEyLC00NTI4MDIwNDQsNj
M3MjE4Mzg3LDEzNzA3MDMyNDUsMTA3NzI2MjI1OSwyNTY2MjA4
NDQsMTA5NjE1MjY5LC0zOTc3Mzc5MzUsMjAxNjkxMTE3MCwtMT
MxMDQwMTkwMCwxNjEwMTg3NzU1LC02MTg1NzY3MzUsLTE4MDU2
MDkwNDddfQ==
-->