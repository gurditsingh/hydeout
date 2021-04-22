## What is Data Skew?
Data skew is not an issue with Spark, rather it is a data problem. The cause of the data skew problem is the uneven distribution of the underlying data.

Data skew happens when a small percentage of partitions get most of the data being processed. In normal usage, Spark will generally make sure that the data is evenly split across all tasks, so there isn't a big risk of skew. When you do a join or aggregation, however, Spark distributes the data by key, so that data the same keys goes to the same Node or task. If you have a lot of rows with the same key, then you have some tasks with those keys taking much longer than the others.

### For Example :
Suppose we have four partitions of data as below and when they come in at 128 MB each they are roughly the same size in terms of number of records and number of MBs. However, once we perform a group by city, the first 3 cities are roughly uniform but the last city is significantly larger than other cities which results in a data skewness (uneven distribution of records in partitions)

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-data-skew.png?raw=true)

 - The skewed partition/task (City D) will take more time as compared to other cities.
 - The skewed task take more memory as compared to other cities.
 - The single skewed task will impact the whole stage. because spark execute 4 partitions/task simultaneously and wait to complete the whole stage.

### challenge :
Let's assume one task is taking the maximum amount of data like 70-80 percent to the entire data.

 - In that situation you actually don't get any benefit if you increase the number of tasks.
 - In that situation if you take larger machines in terms of resources memory, CPU cores and etc but still not get any benefit

## Handling Skewness in spark

## Repartitioning
In spark we have partition types called input, output and shuffle. The input and output partition size are controlled by the partition size of the input data but the shuffle partition is based on the count so naturally and unfortunately we have to do little math to figure out.

**1) Input Partition Sizing :** For input partition spark generally do a great job of taking care of these input partitions(Spark Defaults input partition size is 128MB) but sometimes it doesn't work properly and there's a lot of reasons.

 **Increase Parallelism** Sometimes we need to increase the parallelism of the job. for example let's say I have a big cluster having 100 CPU cores. but I only have 100 megabytes of data for processing. In spark we have 128 megabytes input partition size which will wind up to generate only two partitions. The spark will take only two cores out of 100 cores.
 
 In that case we can down the partition size to one megabyte(Property to change the partition size **`spark.sql.files.maxPartitionBytes`**) so that we can utilize the whole cluster CPU cores.
	 
**spark.conf.set("spark.sql.files.maxPartitionBytes","16777216") -> 16MB**
	
**2) Output Partition Sizing :** The output partition can be used either for change the size of the files or you want to change the composition of the files. To change the size of the files you have a couple different ways either coalesced or repartition.
```scala
	val spark = SparkSession
	...
	val df=spark.read.csv("path")
	...
	// you can pass in any interger value to increase the partition
	df.coalesce(1)
	df.repartition(1)
	// you can pass multiple columns to increase the partition
	df.repartition(col("pk"))
```
**3) Shuffle Partition Sizing :** The default for a shuffle is changed by a count and it's controlled with the flag. The default count is 200. We need to change the count according to the use case e.g. if you have 200 partitions and you have more than 20 GB of data this is the wrong number.

**Basic formula to calculate the shuffle count :**

 ![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark-shuffle.png?raw=true)
 
-----
## Use of Combiner
A **Combiner**, also known as a semi-reducer, is an optional class that operates by accepting the inputs from the Map class and thereafter passing the output key-value pairs to the Reducer class. The main function of a **Combiner** is to summarize the map output records with the same key.

The  `groupByKey`  call makes no attempt at merging/combining values, so it’s an expensive operation. Thus the  `combineByKey`  call is just such an optimization. When using  `combineByKey`  values are merged into one value at each partition then each partition value is merged into a single value.

 - If there are many records of the same key then repartition does not help you out then combiner will be a good option.
 - Combiner decrease the size of the shuffle data and reduces the load during aggregation phase.

**Important :** No matters if your data is skewed or not always good to have combiner. 

----

## Salting
Fixing the data skew problem required salting the data sets — meaning adding randomization to the data to allow it to be distributed more evenly. It also required two-stages of aggregation.

 - Salting is adding some random prefix or suffix in the original key.
 - Let's assume we have a skewed key called `StockBrandFoo` with the randomness of 10 integers, we can create keys like StockBrandFoo_0, StockBrandFoo_1 ... StockBrandFoo_9 here _0,_1 are the salts.
 - Once we created the salted key then we can use in aggregation and key can get spread across multiple nodes due to salting.
 - Next we can do the Two-Phase aggregation. In the first phase we can do the aggregation(we can say partial aggregation) on salted keys. In the second phase we can remove the salt and do the final aggregation on the original keys.

```scala
	val spark = SparkSession
	...

	val sch = StructType(List(
      StructField("pk", DataTypes.StringType),
      StructField("sales", DataTypes.IntegerType)
	    ))
	    
	val df=spark.read.schema(sch).csv("path")

	val addSalt=df.withColumn("salted_pk",concat(col("pk") , lit("_"),substring_index((rand() * 100).cast("String"),".",1)  ))
	 val firstPhase=addSalt.groupBy("salted_pk").agg(sum("sales").as("sum_sales"))


	val removeSalt=firstPhase.withColumn("pk", substring_index(col("salted_pk"),"_",1))
	val secondPhase=removeSalt.groupBy("pk").sum("sum_sales")

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2MjMzODU0MCw4NDM0OTU4NTAsLTExNz
M2MjM2MTQsLTEwMjczMjE4MDcsMTIzNDI4NDQxMiwxNTE1NDk3
MTQ1LC04ODQzMTkwOTQsLTE4NDM1NjY5NjcsLTE0NDMwMTY1OD
AsLTcwNDc2NjYwMiwtNjkwMjgyNjE2LC0zNjAxMzY1OSwxNDgz
NTM0NjkzLDE3NjI5NTkxNTgsLTYwMjk3NzA1OSw0NDc1OTcwNT
YsOTY1OTc1NzIzLDEzNDkwMzIyODgsMTk2NzA4OTI4OSwtNTM5
NjgwNDE0XX0=
-->