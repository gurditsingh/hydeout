## What is window in streaming
Let's say there are events arriving at the source and applied operations individually on each event or on events of one micro batch. But there are many cases when you would want to perform operations over a subset off events and aggregate these events over a time interval.

> where **windows** comes in picture

 - It is a subset off events based on a time interval, so over a period of time you will have multiple windows.
 - The number of events may differ in a window.
 - We can use any timestamp to define this interval (like event time, ingestion time, processing time).
 - Once you have events in the window, you can apply operations (like count, sum, max, min etc.)

### Let's understand this with an example.
**Problem Statement :** Assume we are processing the e-commerce sites events. we want to find the total number of product sold, every five minutes.

**Solution:** We need to group the events by a five minute window and then apply the count as our aggregation operation.

--------02:00--------02:05--------02:10--------02:15--------02:20-------->

Let's use goodbye method and specify five minutes window. We're using pickup time since we want to find the rights. Please don't when they started, this means here we are using even timestamp and then apply the count operation 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NTMwMDY5OTksNDQ5NzQyOCw3OTk3Mz
kxNzIsLTIzNDM4OTQwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwt
MTk2NDI1NzUxOSwtMTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxND
IwNzk4NTYxLDg1NzM0NTM0MiwzOTkzODQzNiwxOTY2NDAyNzc2
LDE4NjM4ODg5OTcsNzUyMjEwMzc1LC0yOTk2NjEyNjksLTE1Mj
IzNDEyODcsLTQ3NDQ2NzEyMSw4NTg2MjA0NjQsNzg3MTI3MjUx
XX0=
-->