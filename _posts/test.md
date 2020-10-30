# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate long number which is monotonically increasing and unique, but not consecutive.
 
 

	>  **Spark Doc :** The generated ID is guaranteed to be monotonically increasing and unique, but not consecutive. The current implementation puts the partition ID in the upper 31 bits, and the record number within each partition in the lower 33 bits. The assumption is that the data frame has less than 1 billion partitions, and each partition has less than 8 billion records.
	
	jhgh
	ghjkghjk
	

 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU5MzY5MjA2NSwzNjMwNDkyOTUsLTIxMj
I0NTgxMDIsLTkwOTc3NDMxMCwxMTQ3NjU0ODMsLTU1ODkwODA3
NywtMTA0ODQ3NTk0NSwtMjA4ODc0NjYxMiwtNDUyODAyMDQ0LD
YzNzIxODM4NywxMzcwNzAzMjQ1LDEwNzcyNjIyNTksMjU2NjIw
ODQ0LDEwOTYxNTI2OSwtMzk3NzM3OTM1LDIwMTY5MTExNzAsLT
EzMTA0MDE5MDAsMTYxMDE4Nzc1NSwtNjE4NTc2NzM1LC0xODA1
NjA5MDQ3XX0=
-->