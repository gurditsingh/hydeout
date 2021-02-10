
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **Processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs
   have a time embedded in them. This time signifies when a given event
   is generated at the source.
   
 - **Ingestion Time :** Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested
   into the system. This time is in between of the event time and
   processing time.

**Processing time :** Processing time is the time tracked using a clock run by the processing engine. In this abstraction of time, time passed is signified by the central clock maintained at the driver.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExMjIwNTYxLDg1NzM0NTM0MiwzOTkzOD
QzNiwxOTY2NDAyNzc2LDE4NjM4ODg5OTcsNzUyMjEwMzc1LC0y
OTk2NjEyNjksLTE1MjIzNDEyODcsLTQ3NDQ2NzEyMSw4NTg2Mj
A0NjQsNzg3MTI3MjUxLC0xODQ3Njk2Mzc3LC0xNjkzMTM4MzUx
LDE2NTYxMzI2MjgsMjQxNzM4NDc3LDY4NDIwNTM3MCwxNjAwND
AzNDMxLC03MjcwMTUwMDcsLTk1OTEzOTI3OCw5ODU2MzU2NTRd
fQ==
-->