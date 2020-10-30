# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate long number which is monotonically increasing and unique, but not consecutive.
 hjhj
 hkjkjk
 Spark Doc : A column expression that generates monotonically increasing 64-bit integers.
The generated ID is guaranteed to be monotonically increasing and unique, but not consecutive. The current implementation puts the partition ID in the upper 31 bits, and the record number within each partition in the lower 33 bits. The assumption is that the data frame has less than 1 billion partitions, and each partition has less than 8 billion records.

 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzI5NDE0MzcsMzYzMDQ5Mjk1LC0yMTIyND
U4MTAyLC05MDk3NzQzMTAsMTE0NzY1NDgzLC01NTg5MDgwNzcs
LTEwNDg0NzU5NDUsLTIwODg3NDY2MTIsLTQ1MjgwMjA0NCw2Mz
cyMTgzODcsMTM3MDcwMzI0NSwxMDc3MjYyMjU5LDI1NjYyMDg0
NCwxMDk2MTUyNjksLTM5NzczNzkzNSwyMDE2OTExMTcwLC0xMz
EwNDAxOTAwLDE2MTAxODc3NTUsLTYxODU3NjczNSwtMTgwNTYw
OTA0N119
-->