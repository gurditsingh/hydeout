Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is Spark Context ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

### Functions of SparkContext in Spark

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_sparkcontext.jpg?raw=true)

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext use to set configuration.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.
 - The SparkContext is used to create the tables and run sql on top of that.
 - The SparkContext is used to register the Spark-Listeners.

## What is Spark Session?
In spark 2.0, we have a new entry point build for DataSet and DataFrame API’s called as Spark-Session which will provides a single point of entry to interact with underlying Spark functionality.

Its a combination of SQLContext, HiveContext and StreamingContext. All the API’s available on those contexts are available on SparkSession also SparkSession has a SparkContext for actual computation and also all the above-mentioned contexts can be accessed using the SparkSession object.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNTIxMTU0MDIsLTE4NjkzNDgyNTIsLT
I4MDEwMDA1NiwtMTI0MzUzMDg1NiwtMjY3OTM1ODMxLDExMTEz
NDM4NzgsMTQ0MjA1MTE3NywtNjM4MTQ2NDMsLTc2NDE4NjY2My
wyNjk1MzUzMzYsLTgwMDM2Nzg3LDE1NDAyNzY1NDksMTY3Mzg4
NTA3NywtMzY2NTA5NTE4LC0xNTE3MTA1MTY2LC01Njc4MTA3ND
YsMTMzMDExMTc1LC0xNjU4MTc4ODM4LDE4NTEyMjg4NDMsMTE4
NTYxNDk1OV19
-->