# Handling Late Data Using Watermarking

## What is Late Data
The data is considered to be late when it arrives to the system after the end of its window. For instance let's suppose we've a window storing items for event time included in 2020-02-02 10:00 - 2020-02-02 10:15 interval. Any item having the event time included in this interval but that comes to the system after the window computation is considered to be on late. 

## But, Why should we care?
In window aggregation Spark automatically takes cares of late data. Every aggregate window is like a bucket i.e. as soon as we receive data for a particular new time window, we automatically open up a bucket and start counting the number of records falling in that bucket. These buckets stay open for data which may even come 2 hours late and it will still update that old bucket and thus incrementing the count.

> Structured Streaming can maintain the intermediate state for partial aggregates for a long period of time such that late data can update aggregates of old windows correctly.

**Problems:**

 - The size of the state will continue to increase over time so number of window are increase to handling all the late events .
 - Some of the late events may not have much business value after a while.
 - Reading/Writing state for every micro batch slower the job execution.  

## Lets see in example what events are late events

Suppose we want to find the total number of product sell in every five minutes.

![Lambda Architecture](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/late_1.jpg?raw=true) 

 - First micro batch contains two events from 04:00 to 04:05.
 - Second micro batch contains two events from 04:05 to 04:10 but one event has late event (in red 04:03)
 
 **How spark know 04:03 is a late event :**   First of all, spark calculates, Max Time from previous batch , the max event time from previous is 04:04. then spark check if any up coming event is smaller than 04:04 is a late event.

> The event is a late event. If it's timestamp is smaller than the max timestamp from the previous batch.

## How state cleanup happens
It is necessary for the system to bound the amount of intermediate in-memory state it accumulates. This means the system needs to know when an old aggregate can be dropped from the in-memory state because the application is not going to receive late data for that aggregate any more.

**Spark introduced watermarking** Watermark is moving threshold of how late the data is expected to be and accordingly the engine can drop old state. You can define the watermark of a query by specifying the event time column and the threshold on how late the data is expected to be in terms of event time.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5ODkwMDk0NSwxNjkzMzg5NjU5LC0zNT
kxNDUzNTksNDc2NDM1MDQ3LC0xMTc1NTM2ODc5LDYyOTgwMjc3
Myw2MjQ2MjAyMTAsMTE5OTMxNDU2MiwtMTI5NTQwMTQ2OCw0Mz
I3Njk3NDcsNTUxMjQ2NjYsNDQ5NzQyOCw3OTk3MzkxNzIsLTIz
NDM4OTQwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwtMTk2NDI1Nz
UxOSwtMTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNzk4NTYx
XX0=
-->