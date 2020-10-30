# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 1. **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate long number which is monotonically increasing and unique, but not consecutive.
 
 

	>  **Spark Doc :** The generated ID is guaranteed to be monotonically increasing and unique, but not consecutive. The current implementation puts the partition ID in the upper 31 bits, and the record number within each partition in the lower 33 bits. The assumption is that the data frame has less than 1 billion partitions, and each partition has less than 8 billion records.
	
	
	
	**Let’s create one job and generate surrogate keys**
	
	```scala
	 def run(args: Array[String]): Unit = {

	    val spark = SparkSession
	      .builder()
	      .master(args(0))
	      .config("spark.sql.warehouse.dir", System.getProperty("user.dir") + "/spark-warehouse")
	      .enableHiveSupport()
	      .getOrCreate()


	    val articles = loadDataFromSource(spark)

	    val attachSurrogateKey = articles.withColumn("sk", functions.monotonically_increasing_id())

	    attachSurrogateKey.write.mode(SaveMode.Overwrite).saveAsTable("articles_tbl")

	  }

	```
	After running this job surrogate keys will generate. But this is kind of what the data looks like. We're gonna do another insert, because the whole idea is this thing is that you know, you're gonna be updating your data in batches, maybe a million at a time, maybe 1000 at a time, and you're gonna be doing this repeatedly. So we want to see how this surrogate key generation performs over multiple inserts.
 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkzNzA1NTg5NiwzNTEyMzY0NDQsLTEyNz
kwMzAwNjksMzYzMDQ5Mjk1LC0yMTIyNDU4MTAyLC05MDk3NzQz
MTAsMTE0NzY1NDgzLC01NTg5MDgwNzcsLTEwNDg0NzU5NDUsLT
IwODg3NDY2MTIsLTQ1MjgwMjA0NCw2MzcyMTgzODcsMTM3MDcw
MzI0NSwxMDc3MjYyMjU5LDI1NjYyMDg0NCwxMDk2MTUyNjksLT
M5NzczNzkzNSwyMDE2OTExMTcwLC0xMzEwNDAxOTAwLDE2MTAx
ODc3NTVdfQ==
-->