
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs
   have a time embedded in them. This time signifies when a given event
   is generated at the source.

**Ingestion Time :** Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested into the system. This time is in between of the event time and processing time.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTc2ODE3NCwzOTkzODQzNiwxOTY2ND
AyNzc2LDE4NjM4ODg5OTcsNzUyMjEwMzc1LC0yOTk2NjEyNjks
LTE1MjIzNDEyODcsLTQ3NDQ2NzEyMSw4NTg2MjA0NjQsNzg3MT
I3MjUxLC0xODQ3Njk2Mzc3LC0xNjkzMTM4MzUxLDE2NTYxMzI2
MjgsMjQxNzM4NDc3LDY4NDIwNTM3MCwxNjAwNDAzNDMxLC03Mj
cwMTUwMDcsLTk1OTEzOTI3OCw5ODU2MzU2NTQsLTE1NDI2MDgy
NTRdfQ==
-->