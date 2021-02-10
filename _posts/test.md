
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **Processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Timestamp at which event happened. Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs have a time embedded in them. This time signifies when a given event is generated at the source.
   
 - **Ingestion Time :** Timestamp at which reaches to source. Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested into the system. This time is in between of the event time and processing time.
 - **Processing time :** Timestamp at which events processed. Processing time is time tracked by processing engine regarding when data was arrived for processing. In this abstraction of time, time passed is signified by the central clock maintained at the driver.

## Let's take an example to understand Time
![Example](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/Streaming.jpg?raw=true)

 - Assume smart watch generating some events regarding number of steps, in the event it specifies unique ID, and Timestamp , let's say time is 2 a.m. So this timestamp at which the event actually happened is called the event or application time, and this timestamp is present in the payload itself.
 - So next  sends this event to the streaming source like Azure Event-Hubs assume that it took one second for the event to reach the source.
 - 
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NjgwMTUyMjgsODkzMTkwODI5LC0xOT
Y0MjU3NTE5LC0xNzIwMzM0OTU5LC0xMDU2NjcyMTkyLDE0MjA3
OTg1NjEsODU3MzQ1MzQyLDM5OTM4NDM2LDE5NjY0MDI3NzYsMT
g2Mzg4ODk5Nyw3NTIyMTAzNzUsLTI5OTY2MTI2OSwtMTUyMjM0
MTI4NywtNDc0NDY3MTIxLDg1ODYyMDQ2NCw3ODcxMjcyNTEsLT
E4NDc2OTYzNzcsLTE2OTMxMzgzNTEsMTY1NjEzMjYyOCwyNDE3
Mzg0NzddfQ==
-->