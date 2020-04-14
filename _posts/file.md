
# The Situation: Data on Data Lakes

Enterprises started collecting their data into the data lakes and they were collecting clickstream data images videos and oftentimes they were actually doing this with Apache spark and the promise was that once they have all this data in their data lakes they can get to all kinds of use cases on top of those they can do data science they can do machine learning they can even do maybe real-time streaming with it so they're kept collecting this data into data lakes.

# The problem with Data Lakes:

Many of the projects are actually falling and whats happening is basically you could say garbage in garbage out.

**Messy data:** what happens if messy data enters the system? “Garbage” data is stored and it is impossible to extract needed or wanted value. How to fix this problem? You can create new Spark jobs to validate the data.

**Failed jobs:** Failed jobs leave data in corrupt state. This requires tedious data cleanup after failed jobs.

**Mistakes and failure:** Even with validation jobs there is always room for error. You need to make sure that it is possible to reprocess part of the data if any error is found then we just simply delete corrupt data and start loading it again.

**File size inconsistency:** Either too small or too big files. Having too many files causes workers to spend more time accessing, opening and closing files when reading which affects performance.

# Basic project architecture
Set of events that are coming in to Kafka or Kinesis and you want to do a bunch of different things with it you want to do some streaming analytics you also want to do some kind of more intense AI and reporting on the historical data. we can use apache spark it's going to read from Kafka and do streaming analytics. next pipeline archive the data into data lake for reporting great that's pretty easy structured streaming works. 
![Flow](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/datalake.jpg?raw=true)

## Big Question ?
how do you architect this thing to achieve analytics and reporting.



# let's go ahead and start.

**Start with basic streaming pipeline** 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUwOTQyOTUyMSwtMzE5MDg2NzAwLC02OT
k4MjIwOCwtNzM5MzkwODMxLC03MDc1NzE4MzEsLTU5MjQ1NDM3
NiwxNDM4NDMwMTE3LDk0MzA4MDI3M119
-->