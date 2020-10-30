# How to create a surrogate key with Apache Spark

 **What does  Surrogate Key  mean?**
 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

# Let's examine what are the options available in Spark

 - **monotonically_increasing_id :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use monotonically_increasing_id method to generate long number which is monotonically increasing and unique, but not consecutive.
 
 

	>  **Spark Doc :** The generated ID is guaranteed to be monotonically increasing and unique, but not consecutive. The current implementation puts the partition ID in the upper 31 bits, and the record number within each partition in the lower 33 bits. The assumption is that the data frame has less than 1 billion partitions, and each partition has less than 8 billion records.
	
	
	
	**Let’s create a sample job (Job-1) to generate surrogate keys**
	
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

	    attachSurrogateKey.write.mode(SaveMode.Append).saveAsTable("articles_tbl")

	  }

	```
	After running this job surrogate keys will generate. But in ETL jobs we going to be updating the data in batches, maybe a million at a time, maybe 1000 at a time. So we want to see how this surrogate key generation performs over multiple inserts.

	> Run the same job one more time and see how surrogate keys are generated : so when we run the same job again it generates the duplicate surrogate keys.

	**Lets understand with Example**: 
	

 - In First run we insert 1million records and spark generates unique 1million surrogate keys.
 - In Second run we insert 1 million records with append mode it generates duplicates surrogates keys.
 
	**What is the reason for this massive amount of surrogates keys collisions/duplication ?**
	The thing is with monotonically increasing ID is, it returns a number between zero and some upper bound. And it only guarantees that the numbers are increased monotonically. So there's no guarantee you'll generate the same numbers or won't generate the same for next batches.

	**Possible Solution :** Since monotonically increasing ID starts with zero, we're going to add max value to it. And so we're gonna do this all over again. So we will take the max value Plus a range of IDs to generate SK for the second and subsequent attempts and by this we've achieved uniqueness, which is a very important criteria in surrogate keys.
	
 
	 **Let’s create a sample job (Job-2) to generate surrogate keys with max value**
	```scala
	def run(args: Array[String]): Unit = {

	    val spark = SparkSession
	      .builder()
	      .master(args(0))
	      .config("spark.sql.warehouse.dir", System.getProperty("user.dir") + "/spark-warehouse")
	      .enableHiveSupport()
	      .getOrCreate()

	    val articles = loadDataFromSource(spark)

	    val maxValueOfSK = if (spark.catalog.tableExists("articles_tbl"))
	      spark.read.table("articles_tbl").groupBy().max("sk").collect() match {
	        case Array() => 0L
	        case a => a.head.get(0).asInstanceOf[Long]
	      }
	    else 0L


	    val attachSurrogateKey = articles.withColumn("sk", functions.monotonically_increasing_id().+(maxValueOfSK))

	    attachSurrogateKey.write.mode(SaveMode.Append).saveAsTable("articles_tbl")

	    spark.read.table("articles_tbl").show()

	  }
	```
	 So the good news is that we have distribution and uniqueness. 

	**Evaluation of monotonically_increasing_id()**
	

	 - Uniqueness : By using second job (job-2) we have achieved uniqueness.
	 - Evenly Distributed : Both the jobs are evenly distributed.
	 - DBA Perspective : I think that the DBA is going to probably complain about the maximum surrogate key value here is way larger than total number of records. e.g. if your table contains 1 million records but the max value of surrog
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkyNDg3NDcyNCw2NTkyNTY5OTYsMTE5Nj
EyMjIwLC0xMzQxODczMjIxLDIxMTQ5ODEyMjksMTc3NzUwNzky
NCwyNjcxMzYzOSwxOTM3MDU1ODk2LDM1MTIzNjQ0NCwtMTI3OT
AzMDA2OSwzNjMwNDkyOTUsLTIxMjI0NTgxMDIsLTkwOTc3NDMx
MCwxMTQ3NjU0ODMsLTU1ODkwODA3NywtMTA0ODQ3NTk0NSwtMj
A4ODc0NjYxMiwtNDUyODAyMDQ0LDEzNzA3MDMyNDUsMjU2NjIw
ODQ0XX0=
-->