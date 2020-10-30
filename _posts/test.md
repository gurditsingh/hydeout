# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add row number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate incremental numbers. However the numbers won’t be consecutive if the dataframe has more than 1 partition. Let’s see a simple example to understand it

 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzYzMDQ5Mjk1LC0yMTIyNDU4MTAyLC05MD
k3NzQzMTAsMTE0NzY1NDgzLC01NTg5MDgwNzcsLTEwNDg0NzU5
NDUsLTIwODg3NDY2MTIsLTQ1MjgwMjA0NCw2MzcyMTgzODcsMT
M3MDcwMzI0NSwxMDc3MjYyMjU5LDI1NjYyMDg0NCwxMDk2MTUy
NjksLTM5NzczNzkzNSwyMDE2OTExMTcwLC0xMzEwNDAxOTAwLD
E2MTAxODc3NTUsLTYxODU3NjczNSwtMTgwNTYwOTA0NywtNzQ3
MzA0NDA1XX0=
-->