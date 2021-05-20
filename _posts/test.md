Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms(functionalities) around the spark-submit and Livy.

## What is SparkContext ?


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExOTU2MzIwOSwtNzY0MTg2NjYzLDI2OT
UzNTMzNiwtODAwMzY3ODcsMTU0MDI3NjU0OSwxNjczODg1MDc3
LC0zNjY1MDk1MTgsLTE1MTcxMDUxNjYsLTU2NzgxMDc0NiwxMz
MwMTExNzUsLTE2NTgxNzg4MzgsMTg1MTIyODg0MywxMTg1NjE0
OTU5LC05NTYyMjQwMTYsLTg0NDY3NTk3NCwtMTMwMDQwMjYzNC
wtODQyMjcwMDc2LDE5MDA5ODMzNTYsLTE1MTA3NDM0NTMsMTU4
NTIwNTg0M119
-->