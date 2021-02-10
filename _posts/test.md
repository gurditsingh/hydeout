
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **Processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Timestamp at which event happened. Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs have a time embedded in them. This time signifies when a given event is generated at the source.
   
 - **Ingestion Time :** Timestamp at which reaches to source. Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested into the system. This time is in between of the event time and processing time.
 - **Processing time :** Timestamp at which events processed. Processing time is time tracked by processing engine regarding when data was arrived for processing. In this abstraction of time, time passed is signified by the central clock maintained at the driver.

## Let's take an example to understand Time


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MjAzMzQ5NTksLTEwNTY2NzIxOTIsMT
QyMDc5ODU2MSw4NTczNDUzNDIsMzk5Mzg0MzYsMTk2NjQwMjc3
NiwxODYzODg4OTk3LDc1MjIxMDM3NSwtMjk5NjYxMjY5LC0xNT
IyMzQxMjg3LC00NzQ0NjcxMjEsODU4NjIwNDY0LDc4NzEyNzI1
MSwtMTg0NzY5NjM3NywtMTY5MzEzODM1MSwxNjU2MTMyNjI4LD
I0MTczODQ3Nyw2ODQyMDUzNzAsMTYwMDQwMzQzMSwtNzI3MDE1
MDA3XX0=
-->