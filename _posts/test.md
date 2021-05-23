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

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_spark_session.jpg?raw=true)

### Need of Spark session when Spark already have Spark context?

 - Spark session unifies all the different contexts in spark and avoids the developer to worry about creating difference contexts.
 - Spark session helps when we have multiple users and they want to share the same spark context.

**lets understand by code:**
Suppose we have multiple users and they want to share the Notebook

 - All have there own set of Configurations.
 - All have there own set of Tables.

```scala
val oldSession=spark
oldSession: org.apache.spark.sql.SparkSession = org.apache.spark.sql.SparkSession@3b0994ad

val newSession=spark.newSession
newSession: org.apache.spark.sql.SparkSession = org.apache.spark.sql.SparkSession@46d15164
```

Spark gives a straight forward API to create a new session which shares the same spark context.`spark.newSession()` creates a new spark session object. if you check oldSession and newSession they have different hashcodes.

```scala
oldSession.sparkContext
res2: org.apache.spark.SparkContext = org.apache.spark.SparkContext@e073b56

newSession.sparkContext
res3: org.apache.spark.SparkContext = org.apache.spark.SparkContext@e073b56
```
But if we check sparkContext under both the sessions(oldSession, newSession) have the same hashcode. so if we create temp table under the oldSessionand newSession they will be not shared with each other. Check out the complete [Source code](https://github.com/gurditsingh/blog/blob/gh-pages/files/TestSparkSession.html "Source code").


## Spark Submit
The **spark-submit** script in Spark’s bin directory is used to launch applications on a cluster. It can use all of Spark’s supported cluster managers through a uniform interface to configure and run the applications on cluster.

The **spark-submit** command is a utility to run or submit a Spark application program (or job) to the cluster by specifying options and configurations. The application you are submitting can be written in Scala, Java, or Python (PySpark).

**where is spark-submit :**
Spark binary comes with **spark-submit.sh** script file for Linux, Mac, and `spark-submit.cmd` command file for windows, these scripts are available at **$SPARK_HOME/bin** directory.

Below is a spark-submit command with the commonly used options.
```bash
./bin/spark-submit \
  --master <master-url> \
  --deploy-mode <deploy-mode> \
  --conf <key<=<value> \
  --driver-memory <value>g \
  --executor-memory <value>g \
  --executor-cores <number of cores>  \
  --jars  <comma separated dependencies>
  --class <main-class> \
  <application-jar> \
  [application-arguments]
```

### How we use spark-submit
In the below diagram we have edge node and cluster. The Edge node is used by user to run the application. The edge node 

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spt_ep4_sparksubmit.jpg?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3NzA2MDM3NywtMjExNzM0NDIxMCwtMj
E2Nzg1NjUsMzMwNzI1NTk2LDE5MTQxNDUwOTksLTEwODA3NDU5
MzIsLTE3MDk3OTg4NzYsLTEyNTIxMTU0MDIsLTE4NjkzNDgyNT
IsLTI4MDEwMDA1NiwtMTI0MzUzMDg1NiwtMjY3OTM1ODMxLDEx
MTEzNDM4NzgsMTQ0MjA1MTE3NywtNjM4MTQ2NDMsLTc2NDE4Nj
Y2MywyNjk1MzUzMzYsLTgwMDM2Nzg3LDE1NDAyNzY1NDksMTY3
Mzg4NTA3N119
-->