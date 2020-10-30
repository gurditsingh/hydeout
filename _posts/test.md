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
	After running this job surrogate keys will generate. But in ETL jobs we going to be updating the data in batches, maybe a million at a time, maybe 1000 at a time. So we want to see how this surrogate key generation performs over multiple inserts.

	> Run the same job one more time and see how surrogate keys are generated : so when we run the same job again it generates the duplicate surrogate keys.

	Lets understand with Ex: suppose First run we insert 1million records with unique 1million surrogate keys
 
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU3MzQ0MDUzLDE5MzcwNTU4OTYsMzUxMj
M2NDQ0LC0xMjc5MDMwMDY5LDM2MzA0OTI5NSwtMjEyMjQ1ODEw
MiwtOTA5Nzc0MzEwLDExNDc2NTQ4MywtNTU4OTA4MDc3LC0xMD
Q4NDc1OTQ1LC0yMDg4NzQ2NjEyLC00NTI4MDIwNDQsMTM3MDcw
MzI0NSwyNTY2MjA4NDQsMTA5NjE1MjY5LC0zOTc3Mzc5MzUsMj
AxNjkxMTE3MCwxNjEwMTg3NzU1LC02MTg1NzY3MzUsLTE4MDU2
MDkwNDddfQ==
-->