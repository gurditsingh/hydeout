Spark framework provides spark-submit command to submit Spark batch jobs and spark-shell for interactive jobs.  Apache Livy Server is provides similar functionality via REST API call to run Spark jobs.

In this blog we will examine how spark-submit works and how Apache Livy as REST API works to submit jobs, monitor the progress of the job and kill the job. First lets look the terms() around the spark-submit and Livy.

What is SparkContext ?

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTQwOTUzODM2LC03NjQxODY2NjMsMjY5NT
M1MzM2LC04MDAzNjc4NywxNTQwMjc2NTQ5LDE2NzM4ODUwNzcs
LTM2NjUwOTUxOCwtMTUxNzEwNTE2NiwtNTY3ODEwNzQ2LDEzMz
AxMTE3NSwtMTY1ODE3ODgzOCwxODUxMjI4ODQzLDExODU2MTQ5
NTksLTk1NjIyNDAxNiwtODQ0Njc1OTc0LC0xMzAwNDAyNjM0LC
04NDIyNzAwNzYsMTkwMDk4MzM1NiwtMTUxMDc0MzQ1MywxNTg1
MjA1ODQzXX0=
-->