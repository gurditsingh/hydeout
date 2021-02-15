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
----
**Remember**

> same windows will be generated irrespective of when the processing happens. Whether you have trigger interval or 5 seconds, 10 seconds, 5 minute or 10 minutes. It does not matter. It will still generate the same windows. Since we're grouping based on event time.

## There are different types of windows

 - **Tumbling windows** are a series of fixed or equal sized windows, non-overlapping and contiguous time intervals.

	Tumbling windows are the norm when we need to produce aggregates of our data over regular periods of time, with each period independent from previous periods.

	**sample code:**
	```scala
	prdouctDF
		.groupBy(window($"productTime", "5 minute"))
	    .count()
	```
	----
	**Basic Example:**
	

 - Batch 1 have two records between 01:00 to 01:05.
 - Batch 2 have three records 

	 
	![Lambda Architecture](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/TumblingWindows.jpg?raw=true) 
		
	

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQxNDk5NjkzLDYyNDYyMDIxMCwxMTk5Mz
E0NTYyLC0xMjk1NDAxNDY4LDQzMjc2OTc0Nyw1NTEyNDY2Niw0
NDk3NDI4LDc5OTczOTE3MiwtMjM0Mzg5NDAsLTIwODI5NTMyND
AsODkzMTkwODI5LC0xOTY0MjU3NTE5LC0xNzIwMzM0OTU5LC0x
MDU2NjcyMTkyLDE0MjA3OTg1NjEsODU3MzQ1MzQyLDM5OTM4ND
M2LDE5NjY0MDI3NzYsMTg2Mzg4ODk5Nyw3NTIyMTAzNzVdfQ==

-->