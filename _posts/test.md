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

In code we use groupBy method and specify five minutes window. We're using productSold time, this means here we are using event time and then apply the count operation.
```scala
prdouctDF
	.groupBy(window($"productTime", "5 minute"))
    .count()
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTUxMjQ2NjYsNDQ5NzQyOCw3OTk3MzkxNz
IsLTIzNDM4OTQwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwtMTk2
NDI1NzUxOSwtMTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNz
k4NTYxLDg1NzM0NTM0MiwzOTkzODQzNiwxOTY2NDAyNzc2LDE4
NjM4ODg5OTcsNzUyMjEwMzc1LC0yOTk2NjEyNjksLTE1MjIzND
EyODcsLTQ3NDQ2NzEyMSw4NTg2MjA0NjQsNzg3MTI3MjUxXX0=

-->