Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_sparkcontext.jpg?raw=true)

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.
 - The SparkContext is used to create the tables and run sql on top of that.

## What is SparkContext ?
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTMyNDUzNTksLTI2NzkzNTgzMSwxMT
ExMzQzODc4LDE0NDIwNTExNzcsLTYzODE0NjQzLC03NjQxODY2
NjMsMjY5NTM1MzM2LC04MDAzNjc4NywxNTQwMjc2NTQ5LDE2Nz
M4ODUwNzcsLTM2NjUwOTUxOCwtMTUxNzEwNTE2NiwtNTY3ODEw
NzQ2LDEzMzAxMTE3NSwtMTY1ODE3ODgzOCwxODUxMjI4ODQzLD
ExODU2MTQ5NTksLTk1NjIyNDAxNiwtODQ0Njc1OTc0LC0xMzAw
NDAyNjM0XX0=
-->