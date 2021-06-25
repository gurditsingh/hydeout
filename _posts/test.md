
## Problem
Nowadays the schema of the data is constantly evolving and changing because of business needs. To cater all the business requirements and problems the system should constantly evolving the schema and validate the schema. We need some system which validate and evolve the schema because the data is changing very frequently.

## Solution
Delta Lake provide a good way to handle the schema changes. Delta lake on spark store the data on DataFrames and every DataFrame in Spark contains a schema. Delta Lake handle the schema related changes out of the box and provide features like **Schema Enforcement** and **Scheme Evolution**.

 - Delta Lake internally maintain the transaction log for all the management and schema is also store on transaction logs (in JSON files under the metadata)
 - Delta Lake facilitates Schema Enforcement to ensure rejecting writes to the table which has mismatch data schema with the table schema.
 - Delta Lake facilitates Scheme Evolution which allow to users to easily change the table schema to accommodate the new data with new schema (either add new columns or remove old columns).
 

# Lets examine the Schema Enforcement and Scheme Evolution

## 1. Schema Enforcement

In Delta Lake the schema enforcement also known as schema validation which in ensure the data quality in delta lake tables. Delta Lake uses schema validation/enforcement on write. When any new data comes first its checked for data compatibility with with the target table schema at the time of writing. If the schema is not matched with the target table Delta Lake reject the transaction and raise the exception schema mismatch.

 To determine whether the schema is compatible, Delta Lake uses the following there rule:
 
 - Delta Lake ensure that no addional columns present in data with respect to table schema.
 - Delta Lake ensure the  data type for each column with respect to table schema.
 - Delta Lake ensure the column names with respect to table schema.

### Let's Understand the Schema Enforcement by two ways

 1. **How Schema Enforcement works with parquet format**
 
	 Let first create a new parquet table with the parquet file.
	```scala
	val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
	val target_path ="/FileStore/tables/parquetSchemaEnforcement"

	spark.read.parquet(source_path).write.format("parquet").save(target_path)
	spark.read.parquet(target_path).createOrReplaceTempView("parquet_tbl")
	```
	Next print the schema of the parquet table.
	```scala
	spark.read.format("parquet").load(target_path).printSchema

	root
	 |-- state: string (nullable = true)
	 |-- count: integer (nullable = true)
	```
	Next lets check how many rows are in the table. Perform count operation on the parquet table.
	```scala
	spark.sql("select count(*) from parquet_tbl").show()

	+--------+
	|count(1)|
	+--------+
	|      52|
	+--------+

	```
	Next Let start appending some new data using Structured Streaming into the parquet table. We will generate a stream of data from the randomly generated states and dummy count.

	```scala
	import org.apache.spark.sql.streaming.{OutputMode, Trigger}
	import org.apache.spark.sql.types.{DataTypes, StructField, StructType}
	import org.apache.spark.sql.functions._
	import scala.util.Random

	def generate_dummy_stream(tablePath:String,checkpointPath:String,streamName:String)
	{
	  val stateGen = () => {
	    val rand = new Random()
	    val gen = List("CA", "WA","IA")
	    gen.apply(rand.nextInt(3))
	  }

	  def random_dir(): String = {
	    val r = new Random()
	    checkpointPath+"chk/chk_pointing_" + r.nextInt(10000)
	  }

	  val df = spark.readStream.format("rate").option("rowsPerSecond", 1).load()

	  val state_gen = spark.udf.register("stateGen", stateGen)

	  val new_df = df.withColumn("state", state_gen())
	    .withColumn("count", lit(1))


	  new_df.writeStream
	    .queryName(streamName)
	    .trigger(Trigger.ProcessingTime("5 seconds"))
	    .format("parquet")
	    .option("path", tablePath)
	    .option("checkpointLocation", random_dir())
	    .start()
	}
	```

	```scala
	generate_dummy_stream(target_path,"/checkpoint_parquet","StreamOfData")
	```

	After generating the more data lets print the schema again of the parquet table. if you see in the below result we will get different schema as compared to previous state of the table. This happens due to streaming job because stream job add extra column's to the data.
	```scala
	spark.read.format("parquet").load(target_path).printSchema

	root
	 |-- timestamp: timestamp (nullable = true)
	 |-- value: long (nullable = true)
	 |-- state: string (nullable = true)
	 |-- count: integer (nullable = false)
	```
	Next lets check how many rows are in the table after the streaming job. In the below it shows the same count as compared to previous results.
	```scala
	spark.sql("select count(*) from parquet_tbl").show()

	+--------+
	|count(1)|
	+--------+
	|      52|
	+--------+
	```
	lets check how many rows are in the table after the streaming job through spark API. In the below it shows the different count as compared to above results.
	```scala
	spark.read.format("parquet").load(target_path).count()

	res10: Long = 127
	```

	**Observations for Parquet format :**
	
	 - At the starting when we first time load the data into parquet table/path it has 54 records and two columns.
	 - After running the streaming job we load more data to the same parquet table/path.
	 - Streaming job add more columns to the parquet table/path without giving any notification to the user or not fail the job due to schema mismatch.
	 - When user reads the data its not consistent and atomic. because when we ran the count query it will give two different results.
	 - Under the target path parquet table has data with two different schemas. When someone reads from the target path it will not give you the correct results.

2.  **How Schema Enforcement works with Delta format**

	 Let first create a new parquet table with the parquet file.
	```scala
	val source_path = "/FileStore/tables/testData/part_00000_67f679a1_1d91_4571_9d54_54ab84497267_c000_snappy.parquet"
	val target_path ="/FileStore/tables/deltaSchemaEnforcement"

	spark.read.parquet(source_path).write.format("delta").save(target_path)
	spark.read.format("delta").load(target_path).createOrReplaceTempView("delta_tbl")
	```
		
	Next print the schema of the parquet table.
	```scala
	spark.read.format("delta").load(target_path).printSchema

	root
	 |-- state: string (nullable = true)
	 |-- count: integer (nullable = true)
	```
	Next lets check how many rows are in the table. Perform count operation on the parquet table.
	```scala
	spark.sql("select count(*) from delta_tbl").show()

	+--------+
	|count(1)|
	+--------+
	|      52|
	+--------+

	```
	Next Let start appending some new data using Structured Streaming into the delta table. We will generate a stream of data from the randomly generated states and dummy count.

	```scala
	import org.apache.spark.sql.streaming.{OutputMode, Trigger}
	import org.apache.spark.sql.types.{DataTypes, StructField, StructType}
	import org.apache.spark.sql.functions._
	import scala.util.Random

	def generate_dummy_stream(tablePath:String,checkpointPath:String,streamName:String)
	{
	  val stateGen = () => {
	    val rand = new Random()
	    val gen = List("CA", "WA","IA")
	    gen.apply(rand.nextInt(3))
	  }

	  def random_dir(): String = {
	    val r = new Random()
	    checkpointPath+"chk/chk_pointing_" + r.nextInt(10000)
	  }

	  val df = spark.readStream.format("rate").option("rowsPerSecond", 1).load()

	  val state_gen = spark.udf.register("stateGen", stateGen)

	  val new_df = df.withColumn("state", state_gen())
	    .withColumn("count", lit(1))


	  new_df.writeStream
	    .queryName(streamName)
	    .trigger(Trigger.ProcessingTime("5 seconds"))
	    .format("parquet")
	    .option("path", tablePath)
	    .option("checkpointLocation", random_dir())
	    .start()
	}
	```

	```scala
	generate_dummy_stream(target_path,"/checkpoint_parquet","StreamOfData")
	```
	After calling the above function delta lake throw an exception `org.apache.spark.sql.AnalysisException: A schema mismatch detected when writing to the Delta table`

	**Observations for Delta format :**
	
	 - At the starting when we first time load the data into Delta table/path it has 54 records and two columns.
	 - After running the streaming job we try to load more data to the same Delta table/path.
	 - While adding more data Delta Lake throw an **schema mismatch exception** because Streaming job try to change the schema and try to add more columns to the Delta table/path. Delta Lake fail the job due to schema mismatch.
	 - When user reads the data its consistent and atomic. There are no partial files because Delta lake writes the files once the transaction is completed successfully.

## 2. Scheme Evolution
Schema evolution is a feature which allow to easily change the schema of Delta table to accommodate new data over the time. This feature automatically adapt the new schema either to include new columns or remove old columns. Mostly schema evolution is used when you are performing an append or overwrite operation on the Delta table.

### Let's Understand by code
To fix 

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep3.jpg?raw=true)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MjA4MjcyMzQsLTE4NDA5MTI2NTgsMT
M5MDI3MzQwNywtMTQ5MDc2NDQ3NSwtNDQ0ODc1NTgzLDEwNDQz
NTc1ODksLTE5OTU1OTE2MjEsMTc5NzI0NzkxNiwxODk3MTczOT
MxLDk5Mjk4NDg4OSwtMTE2ODAyNDkwOSwyMTQyMzE3NjcxLC00
MjEyNDQyNzMsLTE3MjI0Nzk0MjIsLTE1NzExMTU2MjIsMzAxOT
gwMTg5LC0yMDA0NTE3MzIyLC0xNjQzMjYxNjQzLC0xOTI4MDA3
NDg5LDc0NzA1OTA3OV19
-->