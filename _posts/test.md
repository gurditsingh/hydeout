## What is window in streaming
Let's say there are events arriving at the source and applied operations individually on each event or on events of one micro batch. But there are many cases when you would want to perform operations over a subset off events and aggregate these events over a time interval.

> where **windows** comes in picture

 - It is a subset off events based on a time interval, so over a period of time you will have multiple windows.
 - The number of events may differ in a window.
 - We can use any timestamp to define this interval (like event time, ingestion time, processing time).
 - Once you have events in the window, you can apply operations (like count, sum, max, min etc.)
 - 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU3ODY5NjU5LDQ0OTc0MjgsNzk5NzM5MT
cyLC0yMzQzODk0MCwtMjA4Mjk1MzI0MCw4OTMxOTA4MjksLTE5
NjQyNTc1MTksLTE3MjAzMzQ5NTksLTEwNTY2NzIxOTIsMTQyMD
c5ODU2MSw4NTczNDUzNDIsMzk5Mzg0MzYsMTk2NjQwMjc3Niwx
ODYzODg4OTk3LDc1MjIxMDM3NSwtMjk5NjYxMjY5LC0xNTIyMz
QxMjg3LC00NzQ0NjcxMjEsODU4NjIwNDY0LDc4NzEyNzI1MV19

-->