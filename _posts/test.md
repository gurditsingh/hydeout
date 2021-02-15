## What is window in streaming
Let's say there are events arriving at the source and applied operations individually on each event or on events of one micro batch. But there are many cases when you would want to perform operations over a subset off events and aggregate these events over a time interval.

> where **windows** comes in picture

 - It is a subset off events based on a time interval, so over a period of time you will have multiple windows.
 - The number of events may differ in a window.
 - We can use any timestamp to define this interval (like event time, ingestion time, processing time).
 - Once you have events in the window, you can apply operations (like count, sum, max, min etc.)

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQ5NzQyOCw3OTk3MzkxNzIsLTIzNDM4OT
QwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwtMTk2NDI1NzUxOSwt
MTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNzk4NTYxLDg1Nz
M0NTM0MiwzOTkzODQzNiwxOTY2NDAyNzc2LDE4NjM4ODg5OTcs
NzUyMjEwMzc1LC0yOTk2NjEyNjksLTE1MjIzNDEyODcsLTQ3ND
Q2NzEyMSw4NTg2MjA0NjQsNzg3MTI3MjUxLC0xODQ3Njk2Mzc3
XX0=
-->