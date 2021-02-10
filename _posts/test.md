
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **Ingestion Time** and **Processing time**. Every event that is generated and processed has these time stamps associated with it.

 - **Event time :**  Timestamp at which event happened. Event-time is the time embedded in the data itself. Normally the data which we collect from sources like sensors, logs have a time embedded in them. This time signifies when a given event is generated at the source.
   
 - **Ingestion Time :** Timestamp at which reaches to source. Ingestion time is a time captured at the ingestion of data. Ingestion time is the time when events ingested into the system. This time is in between of the event time and processing time.
 - **Processing time :** Timestamp at which events processed. Processing time is time tracked by processing engine regarding when data was arrived for processing. In this abstraction of time, time passed is signified by the central clock maintained at the driver.

## Let's take an example to understand Time
![Example](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/Streaming.jpg?raw=true)

 - Assume wireless sensor generating some events, in that event it specifies unique ID, and Timestamp , let's say time is 2 a.m. when the event is generated. So this timestamp at which the event actually happened is called the event or application time, and this timestamp is present in the payload itself.
 - So next wireless sensor sends this event to the streaming source like Apache kafka assume that it took one second for the event to reach the source (due to some network latency). So the time at which the even reaches the source is known as injection or arrival time.
 
 - Next even though event has reached the source, it will be picked up by spark for possessing only when the job triggers. assume spark took five seconds to kick off the job. This is what is known as processing time.
 - 
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQyOTE0MjMwOSw4OTMxOTA4MjksLTE5Nj
QyNTc1MTksLTE3MjAzMzQ5NTksLTEwNTY2NzIxOTIsMTQyMDc5
ODU2MSw4NTczNDUzNDIsMzk5Mzg0MzYsMTk2NjQwMjc3NiwxOD
YzODg4OTk3LDc1MjIxMDM3NSwtMjk5NjYxMjY5LC0xNTIyMzQx
Mjg3LC00NzQ0NjcxMjEsODU4NjIwNDY0LDc4NzEyNzI1MSwtMT
g0NzY5NjM3NywtMTY5MzEzODM1MSwxNjU2MTMyNjI4LDI0MTcz
ODQ3N119
-->