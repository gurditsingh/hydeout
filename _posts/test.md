
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

**Processing time :** 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3ODE2NzQ4NjEsMzk5Mzg0MzYsMTk2Nj
QwMjc3NiwxODYzODg4OTk3LDc1MjIxMDM3NSwtMjk5NjYxMjY5
LC0xNTIyMzQxMjg3LC00NzQ0NjcxMjEsODU4NjIwNDY0LDc4Nz
EyNzI1MSwtMTg0NzY5NjM3NywtMTY5MzEzODM1MSwxNjU2MTMy
NjI4LDI0MTczODQ3Nyw2ODQyMDUzNzAsMTYwMDQwMzQzMSwtNz
I3MDE1MDA3LC05NTkxMzkyNzgsOTg1NjM1NjU0LC0xNTQyNjA4
MjU0XX0=
-->