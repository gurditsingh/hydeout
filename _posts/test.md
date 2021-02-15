## What is window in streaming
Let's say there are events arriving at the source and applied operations individually on each event or on events of one micro batch. But there are many cases when you would want to perform operations over a subset off events and aggregate these events over a time interval.

> where **windows** comes in picture

 - It is a subset off events based on a time interval, so over a period of time you will have multiple windows.
 - The number of events may differ in a window.
 - you can use any time stamp to define this interval

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNjQxMDIxNDYsNzk5NzM5MTcyLC0yMz
QzODk0MCwtMjA4Mjk1MzI0MCw4OTMxOTA4MjksLTE5NjQyNTc1
MTksLTE3MjAzMzQ5NTksLTEwNTY2NzIxOTIsMTQyMDc5ODU2MS
w4NTczNDUzNDIsMzk5Mzg0MzYsMTk2NjQwMjc3NiwxODYzODg4
OTk3LDc1MjIxMDM3NSwtMjk5NjYxMjY5LC0xNTIyMzQxMjg3LC
00NzQ0NjcxMjEsODU4NjIwNDY0LDc4NzEyNzI1MSwtMTg0NzY5
NjM3N119
-->