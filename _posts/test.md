# Handling Late Data Using Watermarking

## What is Late Data
The data is considered to be late when it arrives to the system after the end of its window. For instance let's suppose we've a window storing items for event time included in 2020-02-02 10:00 - 2020-02-02 10:15 interval. Any item having the event time included in this interval but that comes to the system after the window computation is considered to be on late. 

## But, Why should we care?
In window aggregation Spark automatically takes cares of late data. Every aggregate window is like a bucket i.e. as soon as we receive data for a particular new time window, we automatically open up a bucket and start counting the number of records falling in that bucket. These buckets stay open for data which may even come 5 hours late and it will still update that old bucket and thus incrementing the count.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMzc4OTU0Nyw0NzY0MzUwNDcsLTExNz
U1MzY4NzksNjI5ODAyNzczLDYyNDYyMDIxMCwxMTk5MzE0NTYy
LC0xMjk1NDAxNDY4LDQzMjc2OTc0Nyw1NTEyNDY2Niw0NDk3ND
I4LDc5OTczOTE3MiwtMjM0Mzg5NDAsLTIwODI5NTMyNDAsODkz
MTkwODI5LC0xOTY0MjU3NTE5LC0xNzIwMzM0OTU5LC0xMDU2Nj
cyMTkyLDE0MjA3OTg1NjEsODU3MzQ1MzQyLDM5OTM4NDM2XX0=

-->