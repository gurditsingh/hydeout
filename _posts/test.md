# Handling Late Data Using Watermarking

## What is Late Data
The data is considered to be late when it arrives to the system after the end of its window. For instance let's suppose we've a window storing items for event time included in 2020-02-02 10:00 - 2020-02-02 10:15 interval. Any item having the event time included in this interval but that comes to the system after the window computation is considered to be on late. 

## But, Why should we care?
In window aggregation Spark automatically takes cares of late data. Every aggregate window is like a bucket i.e. as soon as we receive data for a particular new time window, we automatically open up a bucket and start counting the number of records falling in that bucket. These buckets stay open for data which may even come 2 hours late and it will still update that old bucket and thus incrementing the count.

> Structured Streaming can maintain the intermediate state for partial aggregates for a long period of time such that late data can update aggregates of old windows correctly.

## Lets see in example what events are late events

Suppose we want to find the total number of product sell in every five minutes.

![Lambda Architecture](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/late_1.jpg?raw=true) 

 - First micro batch contains two events from 04:00 to 04:

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyMDg5NTk4OCwxNjkzMzg5NjU5LC0zNT
kxNDUzNTksNDc2NDM1MDQ3LC0xMTc1NTM2ODc5LDYyOTgwMjc3
Myw2MjQ2MjAyMTAsMTE5OTMxNDU2MiwtMTI5NTQwMTQ2OCw0Mz
I3Njk3NDcsNTUxMjQ2NjYsNDQ5NzQyOCw3OTk3MzkxNzIsLTIz
NDM4OTQwLC0yMDgyOTUzMjQwLDg5MzE5MDgyOSwtMTk2NDI1Nz
UxOSwtMTcyMDMzNDk1OSwtMTA1NjY3MjE5MiwxNDIwNzk4NTYx
XX0=
-->