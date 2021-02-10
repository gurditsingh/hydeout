
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **Processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Timestamp at which event happened. Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs have a time embedded in them. This time signifies when a given event is generated at the source.
   
 - **Ingestion Time :** Timestamp at which reaches to source. Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested into the system. This time is in between of the event time and processing time.
 - **Processing time :** Timestamp at which events processed. Processing time is time tracked by processing engine regarding when data was arrived for processing. In this abstraction of time, time passed is signified by the central clock maintained at the driver.

## Let's take an example to understand Time
![Example](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/SStime.jpg?raw=true)

 - Assume smart watch generating some events regarding number of steps, in the event it specifies unique ID, and Time.
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNTYyODY2MCwtMTk2NDI1NzUxOSwtMT
cyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNzk4NTYxLDg1NzM0
NTM0MiwzOTkzODQzNiwxOTY2NDAyNzc2LDE4NjM4ODg5OTcsNz
UyMjEwMzc1LC0yOTk2NjEyNjksLTE1MjIzNDEyODcsLTQ3NDQ2
NzEyMSw4NTg2MjA0NjQsNzg3MTI3MjUxLC0xODQ3Njk2Mzc3LC
0xNjkzMTM4MzUxLDE2NTYxMzI2MjgsMjQxNzM4NDc3LDY4NDIw
NTM3MF19
-->