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

In code we use groupby method and specify five minutes window. We're using productSold time, this means here we are using event timestamp and then apply the count operation 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMxNDY1MjE3MSw0NDk3NDI4LDc5OTczOT
E3MiwtMjM0Mzg5NDAsLTIwODI5NTMyNDAsODkzMTkwODI5LC0x
OTY0MjU3NTE5LC0xNzIwMzM0OTU5LC0xMDU2NjcyMTkyLDE0Mj
A3OTg1NjEsODU3MzQ1MzQyLDM5OTM4NDM2LDE5NjY0MDI3NzYs
MTg2Mzg4ODk5Nyw3NTIyMTAzNzUsLTI5OTY2MTI2OSwtMTUyMj
M0MTI4NywtNDc0NDY3MTIxLDg1ODYyMDQ2NCw3ODcxMjcyNTFd
fQ==
-->