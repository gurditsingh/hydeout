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

## Handling Skewness

### Repartitioning
In spark we have partition types called input, output and shuffle. The input and output partition size are controlled by the partition size of the input data but the shuffle partition is based on the count so naturally and unfortunately we have to do little math to figure out.

**1) Input Partition Sizing** For input partition spark generally do a great job of taking care of these input partitions(Spark Defaults input partition size is 128MB) but sometimes it doesn't work properly and there's a lot of reasons.

 - **Increase Parallelism** Sometimes we need to increase the parallelism of the job. for example let's say I have a big cluster having 100 CPU cores. but I only have 100 megabytes of data for processing. In spark we have 128 megabytes input partition size which will wind up to generate only two partitions. The spark will take only two cores out of 200 cores.
 
 

Blinding repartition your data always naïve and effective approach. In which you increase the number of partitions spark RDD or DataFrame. In spark partitions are mapped to tasks. One partition runs on one task. Repartitioning can be done either by number of partitions or provide different keys.

	**Spark Partition Types**
	

	 - Input

		 

	```scala
	val spark = SparkSession
	...
	val df=spark.read.csv("path")
	...
	// you can pass in any interger value to increase the partition
	df.repartition(1)
	// you can pass multiple columns to increase the partition
	df.repartition(col("pk"))
	```
	- Increase the number of partitions using repartition on RDD or DataFrame.
	- The output size of the shuffle data produced by the repartition always be either 128MB or 256MB.  
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTI5NDUwNzUzLC02MDI5NzcwNTksNDQ3NT
k3MDU2LDk2NTk3NTcyMywxMzQ5MDMyMjg4LDE5NjcwODkyODks
LTUzOTY4MDQxNCw4Mzk4MzQyOTEsMTgxMDgwMzM1NywxODcxMz
U0OTA0LDExMjk0Mzg3ODUsMTEyOTc5MDgyNiwxNTM4MjMzMzI0
LC0yMDcwMjMzODY2LDQwMTc5MjkxMSw3MTY1MjAwODgsLTM2Nj
gwNDUwMywtMTcwMDQyODMwMSwxNTEyNDg1MzA4LDEyNzY4NTYy
Nl19
-->