
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

**Processing time :** Processing time is the time tracked using a clock run by the processing engine. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbODU3MzQ1MzQyLDM5OTM4NDM2LDE5NjY0MD
I3NzYsMTg2Mzg4ODk5Nyw3NTIyMTAzNzUsLTI5OTY2MTI2OSwt
MTUyMjM0MTI4NywtNDc0NDY3MTIxLDg1ODYyMDQ2NCw3ODcxMj
cyNTEsLTE4NDc2OTYzNzcsLTE2OTMxMzgzNTEsMTY1NjEzMjYy
OCwyNDE3Mzg0NzcsNjg0MjA1MzcwLDE2MDA0MDM0MzEsLTcyNz
AxNTAwNywtOTU5MTM5Mjc4LDk4NTYzNTY1NCwtMTU0MjYwODI1
NF19
-->