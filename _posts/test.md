# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate long number which is monotonically increasing and unique, but not consecutive.
 hjhj
 hkjkjk
 Spark Doc : 

 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxODMyOTEyMSwzNjMwNDkyOTUsLTIxMj
I0NTgxMDIsLTkwOTc3NDMxMCwxMTQ3NjU0ODMsLTU1ODkwODA3
NywtMTA0ODQ3NTk0NSwtMjA4ODc0NjYxMiwtNDUyODAyMDQ0LD
EzNzA3MDMyNDUsMjU2NjIwODQ0LDEwOTYxNTI2OSwtMzk3NzM3
OTM1LDIwMTY5MTExNzAsMTYxMDE4Nzc1NSwtNjE4NTc2NzM1LC
0xODA1NjA5MDQ3LC03NDczMDQ0MDUsLTE5NjUyMDY2MywtMTAz
MzU3NzE3MF19
-->