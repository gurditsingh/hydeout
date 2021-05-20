Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?
SparkContext is the entry point of Apache Spark functionality. The most important phase of any Spark driver application is to generate SparkContext. It allows your Spark Application to access the Spark Cluster with the help of Resource Managers such as (YARN/Mesos).

 - We can access a cluster by using this SparkContext. The SparkContext will be used to run anything on Executors.
 - The SparkContext contains the configuration information of the application.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4NTgyMDQ2MywtNjM4MTQ2NDMsLTc2ND
E4NjY2MywyNjk1MzUzMzYsLTgwMDM2Nzg3LDE1NDAyNzY1NDks
MTY3Mzg4NTA3NywtMzY2NTA5NTE4LC0xNTE3MTA1MTY2LC01Nj
c4MTA3NDYsMTMzMDExMTc1LC0xNjU4MTc4ODM4LDE4NTEyMjg4
NDMsMTE4NTYxNDk1OSwtOTU2MjI0MDE2LC04NDQ2NzU5NzQsLT
EzMDA0MDI2MzQsLTg0MjI3MDA3NiwxOTAwOTgzMzU2LC0xNTEw
NzQzNDUzXX0=
-->