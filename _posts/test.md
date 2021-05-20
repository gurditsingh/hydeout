Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzODE0NjQzLC03NjQxODY2NjMsMjY5NT
M1MzM2LC04MDAzNjc4NywxNTQwMjc2NTQ5LDE2NzM4ODUwNzcs
LTM2NjUwOTUxOCwtMTUxNzEwNTE2NiwtNTY3ODEwNzQ2LDEzMz
AxMTE3NSwtMTY1ODE3ODgzOCwxODUxMjI4ODQzLDExODU2MTQ5
NTksLTk1NjIyNDAxNiwtODQ0Njc1OTc0LC0xMzAwNDAyNjM0LC
04NDIyNzAwNzYsMTkwMDk4MzM1NiwtMTUxMDc0MzQ1MywxNTg1
MjA1ODQzXX0=
-->