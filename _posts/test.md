Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look 

What is SparkContext ?

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NjQ3OTg1NjIsLTc2NDE4NjY2MywyNj
k1MzUzMzYsLTgwMDM2Nzg3LDE1NDAyNzY1NDksMTY3Mzg4NTA3
NywtMzY2NTA5NTE4LC0xNTE3MTA1MTY2LC01Njc4MTA3NDYsMT
MzMDExMTc1LC0xNjU4MTc4ODM4LDE4NTEyMjg4NDMsMTE4NTYx
NDk1OSwtOTU2MjI0MDE2LC04NDQ2NzU5NzQsLTEzMDA0MDI2Mz
QsLTg0MjI3MDA3NiwxOTAwOTgzMzU2LC0xNTEwNzQzNDUzLDE1
ODUyMDU4NDNdfQ==
-->