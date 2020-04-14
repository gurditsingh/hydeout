
# The Situation: Data on Data Lakes

Enterprises started collecting their data into the data lakes and they were collecting clickstream data images videos and oftentimes they were actually doing this with Apache spark and the promise was that once they have all this data in their data lakes they can get to all kinds of use cases on top of those they can do data science they can do machine learning they can even do maybe real-time streaming with it so they're kept collecting this data into data lakes.

# The problem with Data Lakes:

Many of the projects are actually falling and whats happening is basically you could say garbage in garbage out.

**Messy data:** what happens if messy data enters the system? “Garbage” data is stored and it is impossible to extract needed or wanted value. How to fix this problem? You can create new Spark jobs to validate the data.

**Failed jobs:** Failed jobs leave data in corrupt state. This requires tedious data cleanup after failed jobs.

**Mistakes and failure:** Even with validation jobs there is always room for error. You need to make sure that it is possible to reprocess part of the data if any error is found then we just simply delete corrupt data and start loading it again.

**File size inconsistency:** Either too small or too big files. Having too many files causes workers to spend more time accessing, opening and closing files when reading which affects performance.

# Basic project architecture
Set of events that are coming in to Kafka or Kinesis and you want to do a bunch of different things with it you want to do some streaming analytics you also want to do some kind of more intense AI and reporting on the historical data with data lake.
![Flow](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/datalake.jpg?raw=true)

# Challenges with Design
**Challenge No 1:** Historical Reporting

we can use apache spark it's going to read from Kafka and do streaming analytics. On historical reporting streaming is great it tells you what's happening right now.
> Problem ?
 But it doesn't let me look back in time and do more complicated things like machine learning. 


**lambda architecture save our life** what it's means in addition to running my streaming pipeline that I use for kind of the immediate results I'm also going to run this spark batch pipeline to archive all this data into the data lake and do reporting and machine learning on it.

**Challenge No 2:** Messy Data

We have all the data in data lake which can be used by data scientists for machine learning, reporting and data modeling.

> Problem ?
> data scientists are looking at my data Lake and telling me this data doesn't make any sense it's too messy usually problem with big data.

**Data validation save our life**  to fix this problem we just put validations into all spots in the pipeline now it's really important that we do it in both places because we're running two different pipelines here but again spark has unified API so it's not too hard so we'll add validations to both part and remove the messy data.

**Challenge No 3:** Fixing Mistakes

We have put the validation in our pipelines to clear the messy data but it turns out before I put those validations in place some messy data leaked out.
> Problem ?
some messy data leaked out in data lake. so now I need to figure out and it's hard when all you have is a distributed file system.

**Recompute save our life** we have to partition it by date and build a framework around spark that will allow me to recompute from any if anything goes wrong I'll just blow that whole folder away and recompute it from scratch and by reprocessing fix the mistakes that happened through leak 

**Challenge No 3:** Updates in Data
Now we have clear data in data lake. Next request is we have to go through this data Lake and remove/update all of these customer addresses but keep everything else.

> Problem ?
 so now I have to worry about updates, can you even do that in the data Lake
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcwNzYxMTE4NiwxNzUyMzE5NzMwLC0xMD
g5MjcxNDYyLC0yMDIxODEwMDA0LDEyNzAyNTQ3NjQsLTMxOTA4
NjcwMCwtNjk5ODIyMDgsLTczOTM5MDgzMSwtNzA3NTcxODMxLC
01OTI0NTQzNzYsMTQzODQzMDExNyw5NDMwODAyNzNdfQ==
-->