# How to create a surrogate key with Apache Spark Part-1

## What does Surrogate Key mean?

 A surrogate key (or synthetic key, pseudokey, entity identifier, system-generated key, database sequence number, factless key, technical key, or arbitrary unique identifier) in a database is a unique identifier for either an entity in the modeled world or an object in the database. The surrogate key is not derived from application data, unlike a natural (or business) key which is derived from application data.
 
 **Surrogate key in a Data Warehouse**: Surrogate keys are typically meaningless integers used to connect the fact to the dimension tables of a data warehouse. There are various reasons why we cannot simply reuse our existing natural or business keys.

## Let's examine the zipwithindex 

 - **zipwithindex :** Spark dataframe add unique number is very common requirement especially if you are working on ELT in Spark. You can use zipwithindex method to generate long number. zipwithindex works on rdd and use  `df.rdd.zipWithIndex()` . 

	>  **Spark Doc :** Zips this RDD with its element indices. The ordering is first based on the partition index and then the ordering of items within each partition. So the first item in the first partition gets index 0, and the last item in the last partition receives the largest index. **This method needs to trigger a spark job when this RDD contains more than one partitions.**
	

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

	    val zippedRDD = articles.rdd.zipWithIndex()

	    val combineRDD = zippedRDD.map { case (row, index) =>
	      Row.fromSeq(Array(index) ++ row.toSeq)
	    }

	    val convertedDF = spark.createDataFrame(combineRDD, getSchema())

	    convertedDF.write.mode(SaveMode.Append).saveAsTable("articles_tbl12")

	  }

	```
	After running this job surrogate keys will generate. But in ETL jobs we going to be updating the data in batches, maybe a million at a time, maybe 1000 at a time. So we want to see how this surrogate key generation performs over multiple inserts.

	> Run the same job one more time and see how surrogate keys are generated : so when we run the same job again, it generates the duplicate surrogate keys.

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
	

	 - **Uniqueness :** By using second job (job-2) we have achieved uniqueness.
	 - **Evenly Distributed :** Both the jobs are evenly distributed.
	 - **DBA Perspective :** I think that the DBA is going to probably complain about the maximum value of surrogate key is way larger than total number of records in the table. e.g. if your table contains millions records but the max value of surrogate key can be in trillions because of internal logic of generating monotonically_increasing_id() and in subsequent runs again add max value of monotonically_increasing_id().   
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyODQyOTEwNCwtMzczMzI3NTQ3LDIzNj
kxODQ0NSwtODUxMDgwODU1LC0xOTc1NjgxNTM0LC0yMDM1ODIw
MzQ2LC00NTM4NDYyNjQsLTE4MDgzMzExOTQsNjU5MjU2OTk2LD
ExOTYxMjIyMCwtMTM0MTg3MzIyMSwyMTE0OTgxMjI5LDE3Nzc1
MDc5MjQsMjY3MTM2MzksMTkzNzA1NTg5NiwzNTEyMzY0NDQsLT
EyNzkwMzAwNjksMzYzMDQ5Mjk1LC0yMTIyNDU4MTAyLC05MDk3
NzQzMTBdfQ==
-->