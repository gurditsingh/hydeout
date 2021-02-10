
# Concept of Time in Spark Structured Streaming

A streaming application is an always running application. So in order to understand the behavior of the application over time, we need to take snapshots of the stream in various points. Normally these various points are defined using a time component.

## Types of Time in Structured Streaming
There are three types of time stamps **Event time**, **injection time** and **processing time**. Every event that is generated and processed has these time stamps associated with it.

**Event time : ** 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDc0MDU3OTI3LDM5OTM4NDM2LDE5NjY0MD
I3NzYsMTg2Mzg4ODk5Nyw3NTIyMTAzNzUsLTI5OTY2MTI2OSwt
MTUyMjM0MTI4NywtNDc0NDY3MTIxLDg1ODYyMDQ2NCw3ODcxMj
cyNTEsLTE4NDc2OTYzNzcsLTE2OTMxMzgzNTEsMTY1NjEzMjYy
OCwyNDE3Mzg0NzcsNjg0MjA1MzcwLDE2MDA0MDM0MzEsLTcyNz
AxNTAwNywtOTU5MTM5Mjc4LDk4NTYzNTY1NCwtMTU0MjYwODI1
NF19
-->