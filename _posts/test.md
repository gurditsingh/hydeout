# Handling Late Data Using Watermarking

## What is Late Data
The data is considered to be late when it arrives to the system after the end of its window. For instance let's suppose we've a window storing items for event time included in 2020-02-02 10:00 - 2020-02-02 10:15 interval. Any item having the event time included in this interval but that comes to the system after the window computation is considered to be on late. 

## But, Why should we care?
In window aggregation Spark automatically takes cares of late data. Every aggregate window is like a bucket i.e. as soon as we receive data for a particular new time window, we automatically open up a bucket and start counting the number of records falling in that bucket. These buckets stay open for data which may even come 2 hours late and it will still update that old bucket and thus incrementing the count.

> Structured Streaming can maintain the intermediate state for partial aggregates for a long period of time such that late data can update aggregates of old windows correctly.

## Lets see in example what events are late events

Suppose we want to find the total number of product sell in every five minutes.

![Lambda Architecture](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/late_1.jpg?raw=true) 

 - First micro batch contains two events from 04:00 to 04:05.
 - Second micro batch contains two events from 04:05 to 04:10 but one event has late event (in red 04:03)
 
 **How spark know 04:03 is a late event :**   First of all, spark calculates, Max Time from previous batch , the max event time from previous is 04:04. then spark check if any up coming event 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MDQ4MjE1NzQsMTY5MzM4OTY1OSwtMz
U5MTQ1MzU5LDQ3NjQzNTA0NywtMTE3NTUzNjg3OSw2Mjk4MDI3
NzMsNjI0NjIwMjEwLDExOTkzMTQ1NjIsLTEyOTU0MDE0NjgsND
MyNzY5NzQ3LDU1MTI0NjY2LDQ0OTc0MjgsNzk5NzM5MTcyLC0y
MzQzODk0MCwtMjA4Mjk1MzI0MCw4OTMxOTA4MjksLTE5NjQyNT
c1MTksLTE3MjAzMzQ5NTksLTEwNTY2NzIxOTIsMTQyMDc5ODU2
MV19
-->