## What is Delta Lake?
In the past there are different storage solutions build to solve the common problem of data quality. Many architecture/tools are build to solve the problem. These tools provides many benefits like decoupling the business logic from storage and compute. It means user can scale the compute and storage power up and down but in between this data reliability lost. To provide the data reliability and quality  Delta Lake come into the picture.

Delta Lake is a file-based, open-source storage format that provides ACID transactions, scalable metadata handling, and unifies streaming and batch data processing. It runs on top of your existing data lakes and is compatible with Apache Spark and other processing engines. Delta Lake combine the both worlds OLAP(Online Analytical Processing) and OLTP(Online Transactional Processing) with the horizontal scalability of data lakes.

 - **ACID transactions :** It is really important that the data integrity is maintained in data lake means no more partial or corrupted data. Delta Lake ensures that all data changes written to storage are committed for durability and made visible to readers atomically.
 - **Unified Batch and Stream Processing :** In a Data lake, if we have an use case of both Stream processing and Batch processing it is normal to follow _Lamdba architecture_. But Delta Lake table has the ability to work both in batch and as a streaming source and sink all just work out of the box.
 - **Scalable data and metadata handling :** Delta Lake is built on data lakes, all reads and writes using Spark or other distributed processing engines are inherently scalable to petabyte-scale. Delta Lake leverages Spark to scale out all the metadata processing to handle metadata or large tables.
 - **Time Travel :** The Delta Lake transaction log records details about every change made to data providing a full audit trail of the changes. Data in the data lake will be versioned and snapshots are provided so that you can query them as if that snapshot was the current state of the system. This helps us to revert to older versions of our data lake for Audits, rollbacks and etc.
 - **Schema Enforcement :** Delta Lake automatically prevents the insertion of data with an incorrect schema, i.e. not matching the table schema. It prevents data corruption by preventing the bad data get into the system.
 - **Support for updates, merge and deletes :** Delta Lake supports merge, delete , and update operations to do complex operations. Most of the distributed processing frameworks do not support atomic data modification operations on data lakes.

## How to start with Delta Lake

 - **Databricks Community Edition :** The Databricks Community Edition is the free version of our cloud-based big data platform. Users can access a micro-cluster as well as a cluster manager and notebook environment. You can start with the Databricks environment in which the delta lake packages are pre-installed. 
 - **Set up project :** If you want to build a project using Delta Lake binaries from Maven Central Repository, you can use the following Maven coordinates.
	```xml
	<dependency>
	    <groupId>io.delta</groupId>
	    <artifactId>delta-core_2.12</artifactId>
	    <version>1.0.0</version>
	</dependency>

	```

## Creating your first Delta Table

While creating a Delta table you have to provide the location, which means you are writing files to some storage. All of the files together stored in a directory of a particular structure which make up your table. Which means when we create a Delta table, we are in fact writing files to some storage location.

 - **Writing to Delta Table :** In the below code example, we will first create the Spark Data Frame and then use the write method to save the delta table to storage location.

	```scala
	//Write the Spark DataFrame to Delta table
	val df = spark.range(10)
	df.write.format("delta").save("/delta_store")

	// Write the Spark DataFrame to Delta table partitioned by date
	val added_date = df.withColumn("date",current_date())
	added_date.write.partitionBy("date").format("delta").save("/delta_store")

	// Append new data to your Delta table
	df.write.format("delta").mode(SaveMode.Append).save("/delta_store")
	// Overwrite your Delta table
	df.write.format("delta").mode(SaveMode.Overwrite).save("/delta_store")

	```
 
 - **Reading from Delta Table :** Like writing your Delta table, you can use the DataFrame API to read the same files from your Delta table.
	```scala
	// Read the data from the Delta table location
	spark.read.format("delta").load("/delta_store").show()
	```
	```sql
	%sql
	SELECT * FROM delta.`/delta_store`
	```
 - **Create Delta table in metastore :** we can save the Delta table files into a location managed by the metastore (e.g. /user/warehouse/myTable). If you want to use SQL or control the location of your Delta table.

	```scala
	// Write the data to the metastore defined table as delta_table
	val df = spark.range(10)
	df.write.format("delta").saveAsTable("delta_table")
	```

	```sql
	%sql
	select * from delta_table
	```
 - **Create Delta table using SQL :** user can create the delta table by sql and load the data by sql commands.
	```sql
	%sql
	-- Create a table in the metastore
	CREATE TABLE delta_table (
	 id INTEGER)
	USING DELTA
	LOCATION "/delta_store"
	```

	```scala
	// Create temp table of the DataFrame
	val df = spark.range(10)
	df.createOrReplaceTempView("tmp_view")
	```
	```sql
	%sql
	CREATE TABLE delta_table 
	USING DELTA
	LOCATION "/delta_store"
	AS SELECT * FROM tmp_view;
	```

## What files are kept under the Delta table location
In Delta table creation the LOCATION property that points to the underlying files which make the Delta table special.

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep1.JPG?raw=true)

If we see in the above results of ls command we have bunch of output files in parquet (that we will discuss later) and one directory called **_delta_log**. As we know Delta lake provides number of features like ACID transactions, scalable metadata handling, time travel and others. The Delta lake have achieved these functionalities with the help of _delta_log also known as Delta transaction log.

## What Is the Delta Transaction Log?

The Delta Lake transaction log (also known as the Delta Log) is an ordered record of every change that has been performed on a Delta Lake table.

![Delta lake](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/dl_ep1_tlog.jpg?raw=true)

 - Suppose you have a table called **my_table** underneath table contain the  above shown directory structure on disk.
 - In in table root directory we have the transaction log directory, which is called _delta_log.
 -  Within the _delta_log directory we have multiple versions of json files. These are numbered zero to long max value. these files contain all the transactions or changes that you make to your Delta table.
 - Next we have optional partition directory. if your Delta table is partitioned on some particular column then it will create the directory accordingly like above we have a partition on year column it will create directories year wise.
 - If your table is partitioned then underneath the partition directory it will create the data files which are simple parquet files. And if the table is not partitioned then the data files will create under the table root directory in parquet format.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk0NzYxOTEyMiwtMTAyOTM2MjEzNywtMz
U2NjE5MjA4LC0yMjQ2NDQ5MTgsMTk5MTIwNTE0NywtMTE1NDEz
NTg5NywtMjAyNDMxMDUyNSwtNjgwMzAyOTY5LDEwNDA2ODAxOD
AsMTYzODYzNjgwNywxNjQxOTYxNzg2LC0xNzI3OTg4NjQ5LDE5
MzU3NDA2MSwxNDIyMTU1MTE5LC0xNzE2ODM1NDU1LDQ3MjcyOD
cxNiw1NTA1NDM5MDYsMzExMTg2NjQ4LC03ODIwNjQyNTAsLTIw
ODg3NDY2MTJdfQ==
-->