Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_sparkcontext.jpg?raw=true)

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.
 - The SparkContext is used to create the tables 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ3MzY3ODYyMiwtMjY3OTM1ODMxLDExMT
EzNDM4NzgsMTQ0MjA1MTE3NywtNjM4MTQ2NDMsLTc2NDE4NjY2
MywyNjk1MzUzMzYsLTgwMDM2Nzg3LDE1NDAyNzY1NDksMTY3Mz
g4NTA3NywtMzY2NTA5NTE4LC0xNTE3MTA1MTY2LC01Njc4MTA3
NDYsMTMzMDExMTc1LC0xNjU4MTc4ODM4LDE4NTEyMjg4NDMsMT
E4NTYxNDk1OSwtOTU2MjI0MDE2LC04NDQ2NzU5NzQsLTEzMDA0
MDI2MzRdfQ==
-->