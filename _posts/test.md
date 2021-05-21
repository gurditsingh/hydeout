Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_sparkcontext.jpg?raw=true)

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.
 - The SparkContext 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NjQzMzM4MDIsMTExMTM0Mzg3OCwxND
QyMDUxMTc3LC02MzgxNDY0MywtNzY0MTg2NjYzLDI2OTUzNTMz
NiwtODAwMzY3ODcsMTU0MDI3NjU0OSwxNjczODg1MDc3LC0zNj
Y1MDk1MTgsLTE1MTcxMDUxNjYsLTU2NzgxMDc0NiwxMzMwMTEx
NzUsLTE2NTgxNzg4MzgsMTg1MTIyODg0MywxMTg1NjE0OTU5LC
05NTYyMjQwMTYsLTg0NDY3NTk3NCwtMTMwMDQwMjYzNCwtODQy
MjcwMDc2XX0=
-->