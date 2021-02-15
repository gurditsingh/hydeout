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


 1. **Tumbling window** are a series of fixed or equal sized windows, non-overlapping and contiguous time intervals.

	Tumbling windows are the norm when we need to produce aggregates of our data over regular periods of time, with each period independent from previous periods.

	**sample code:**
	```scala
	prdouctDF
		.groupBy(window($"productTime", "5 minutes"))
	    .count()
	```
	----
	**Basic Example:**
	
	![Tumbling Window](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/TumblingWindows.jpg?raw=true)

	 - Batch 1 have two events between 01:00 to 01:05 so the count is 2.
	 - Batch 2 have three events one record belongs to 01:00 to 01:05 so the count updates to 3. next one event between 01:05 to 01:10. last event between 01:10 to 01:15.
	 - Batch 3 have three events one event belongs to 01:10 to 01:15 so the count updates to 2. next two event between 01:15 to 01:20 so the count is 2.

	> This is how tumbling window works, you have noticed that even if you change the micro batch interval or called trigger interval, it will still produce the same output.
----

 2. **Sliding window:** are aggregates over a period of time that are reported at a higher frequency than the aggregation period itself. As
   such, sliding windows refer to an aggregation with two time
   specifications: the window length and the reporting frequency.

	Sliding windows are also fixed and equal sides windows assume that you have a window size off 10 minutes, so the first window is from 1:00 to 1:10. 

	Along with the window size you also define is sliding interval. Let's assume, it is five minutes. This means even though window sizes, 10 minutes moves or slides by only five minutes, so the next window is from 1:05 to 1:15.

	In sliding window you now have overlapping windows and because of this one event may belong to multiple windows.

	**sample code:**
	```scala
	prdouctDF
		.groupBy(window($"productTime", "10 minutes" , "5 minutes"))
	    .count()
	```
	----
	![Tumbling Window](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/slidingWindow.jpg?raw=true)

	 

	 - Batch 1 have two events between 01:00 to 01:10 so the count is 2.
	 - Batch 2 have three events, one event belongs to 01:00 to 01:10 and update the count to 4. next sliding window moves 5 mins ahead 01:05 to 01:15 and the count is 2. last event 01:10 to 01:20 and count is 1.
	 - Batch 3 have three events, one event belongs to 01:05 to 01:15 and update the count to 3 same for 01:10 to 01:20 update the count to 4. last event 01:15 to 01:25 and count is 2.

	> If you change the micro batch interval, it will still produce these same output.

 ----

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDc2NDM1MDQ3LC0xMTc1NTM2ODc5LDYyOT
gwMjc3Myw2MjQ2MjAyMTAsMTE5OTMxNDU2MiwtMTI5NTQwMTQ2
OCw0MzI3Njk3NDcsNTUxMjQ2NjYsNDQ5NzQyOCw3OTk3MzkxNz
IsLTIzNDM4OTQwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwtMTk2
NDI1NzUxOSwtMTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNz
k4NTYxLDg1NzM0NTM0MiwzOTkzODQzNiwxOTY2NDAyNzc2XX0=

-->