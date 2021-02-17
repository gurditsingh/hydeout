# Handling Late Data Using Watermarking

## What is Late Data
The data is considered to be late when it arrives to the system after the end of its window. For instance let's suppose we've a window storing items for event time included in 2020-02-02 10:00 - 2020-02-02 10:15 interval. Any item having the event time included in this interval but that comes to the system after the window computation is considered to be on late. 

## But, Why should we care?
In window aggregation Spark automatically takes cares of late data. Every aggregate window is like a bucket i.e. as soon as we receive data for a particular new time window, we automatically open up a bucket and start counting the number of records falling in that bucket. These buckets stay open for data which may even come 2 hours late and it will still update that old bucket and thus incrementing the count.

> Structured Streaming can maintain the intermediate state for partial aggregates for a long period of time such that late data can update aggregates of old windows correctly.

## Lets see in example what events are late events

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5NjM5MTY3OSwtMzU5MTQ1MzU5LDQ3Nj
QzNTA0NywtMTE3NTUzNjg3OSw2Mjk4MDI3NzMsNjI0NjIwMjEw
LDExOTkzMTQ1NjIsLTEyOTU0MDE0NjgsNDMyNzY5NzQ3LDU1MT
I0NjY2LDQ0OTc0MjgsNzk5NzM5MTcyLC0yMzQzODk0MCwtMjA4
Mjk1MzI0MCw4OTMxOTA4MjksLTE5NjQyNTc1MTksLTE3MjAzMz
Q5NTksLTEwNTY2NzIxOTIsMTQyMDc5ODU2MSw4NTczNDUzNDJd
fQ==
-->