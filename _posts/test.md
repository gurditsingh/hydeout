Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

 - We can access a cluster by using this SparkContext. The SparkContext 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NzQyNjk0MTEsLTYzODE0NjQzLC03Nj
QxODY2NjMsMjY5NTM1MzM2LC04MDAzNjc4NywxNTQwMjc2NTQ5
LDE2NzM4ODUwNzcsLTM2NjUwOTUxOCwtMTUxNzEwNTE2NiwtNT
Y3ODEwNzQ2LDEzMzAxMTE3NSwtMTY1ODE3ODgzOCwxODUxMjI4
ODQzLDExODU2MTQ5NTksLTk1NjIyNDAxNiwtODQ0Njc1OTc0LC
0xMzAwNDAyNjM0LC04NDIyNzAwNzYsMTkwMDk4MzM1NiwtMTUx
MDc0MzQ1M119
-->