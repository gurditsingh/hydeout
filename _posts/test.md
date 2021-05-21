Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

SparkContext provides various functions in Spark such as get the current status of Spark Application, set the configuration, Cancel a stage, cancel a job, and much more. Thus, it acts as a backbone.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/sep5_sparkcontext.jpg?raw=true)

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - The SparkContext can be used to create RDDs, accumulators and broadcast variables.
 - The SparkContext is used 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2NzkzNTgzMSwxMTExMzQzODc4LDE0ND
IwNTExNzcsLTYzODE0NjQzLC03NjQxODY2NjMsMjY5NTM1MzM2
LC04MDAzNjc4NywxNTQwMjc2NTQ5LDE2NzM4ODUwNzcsLTM2Nj
UwOTUxOCwtMTUxNzEwNTE2NiwtNTY3ODEwNzQ2LDEzMzAxMTE3
NSwtMTY1ODE3ODgzOCwxODUxMjI4ODQzLDExODU2MTQ5NTksLT
k1NjIyNDAxNiwtODQ0Njc1OTc0LC0xMzAwNDAyNjM0LC04NDIy
NzAwNzZdfQ==
-->