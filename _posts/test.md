Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spt_ep4_FileFormat.jpg?raw=true)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjA2MDkxNzkxLDExMTEzNDM4NzgsMTQ0Mj
A1MTE3NywtNjM4MTQ2NDMsLTc2NDE4NjY2MywyNjk1MzUzMzYs
LTgwMDM2Nzg3LDE1NDAyNzY1NDksMTY3Mzg4NTA3NywtMzY2NT
A5NTE4LC0xNTE3MTA1MTY2LC01Njc4MTA3NDYsMTMzMDExMTc1
LC0xNjU4MTc4ODM4LDE4NTEyMjg4NDMsMTE4NTYxNDk1OSwtOT
U2MjI0MDE2LC04NDQ2NzU5NzQsLTEzMDA0MDI2MzQsLTg0MjI3
MDA3Nl19
-->