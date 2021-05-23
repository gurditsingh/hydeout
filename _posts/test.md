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

# Ways to run the job on cluster

## 1. Spark Submit
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

### Basic terminology of cluster
In the below diagram we have edge node and cluster. The Edge node is used by the user (which run the application/job) to run the application on the cluster.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spt_ep4_sparksubmit.jpg?raw=true)

**Edge Node :**

 - The Edge node can be the system used by the user and which is outside of the cluster but have connectivity to the cluster.
 - The Edge node can be system used by the user which is one of the node in the cluster. Generally the driver node can be the edge node.

**Cluster :** 

 - Cluster is consist of number of nodes : number of Master nodes, number of Edge Nodes,
   number of Worker Nodes.
 - In cluster we have configuration of each node: number of cores per node, RAM and
   Disk Volume.

### How to use spark-submit
![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spt_ep4_deploysparksubmit.jpg?raw=true)

 - In dev/qa/prod environment we have edge node and one big cluster which can be on-prem or cloud.
 - First user need to copy all the artifacts like **job**(means java, scala jar ), **files** (can be input files or config files), third party **library** to cluster or edge node.
 - Next from edge node run the job by spark submit. By using spark submit parameters user can submit the job on cluster
 - Spark provides the common utility like spark-submit to run the job/application on cluster.
  
 **Example :**
 ```bash
./bin/spark-submit \
--master yarn \
--deploy-mode cluster \
--conf "spark.sql.shuffle.partitions=1000" \
--jars "dependency1.jar,dependency2.jar"
--class com.test.WordCountExample \
spark-example.jar 
```

## 2. REST API Apache Livy


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg4MTcwOTMyLDE0MjUxMDMxOTIsLTQ3OD
I1MTU0MSwxMzgyMzcwNjAxLDEzMzk5OTE4MjUsLTEwODAwNTAy
ODUsLTIxMTczNDQyMTAsLTIxNjc4NTY1LDMzMDcyNTU5NiwxOT
E0MTQ1MDk5LC0xMDgwNzQ1OTMyLC0xNzA5Nzk4ODc2LC0xMjUy
MTE1NDAyLC0xODY5MzQ4MjUyLC0yODAxMDAwNTYsLTEyNDM1Mz
A4NTYsLTI2NzkzNTgzMSwxMTExMzQzODc4LDE0NDIwNTExNzcs
LTYzODE0NjQzXX0=
-->