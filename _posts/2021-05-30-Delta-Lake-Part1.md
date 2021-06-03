---
title: "Part-1 'Overview' : Delta Lake"
layout: post
excerpt: "In this first part, we will understand What kind of problem it causes for a typical data lake implementation"
last_modified_at: 2021-05-30T11:02:01-05:00
tags:
  - Data Lakes
  - Spark
  - Cloud
  - Lambda
---


# The Situation: Data on Data Lakes

Enterprises started collecting their data into the data lakes and they were collecting log data, transaction data, clickstream data, images, and etc. oftentimes they were actually doing this with Apache spark and the promise was that once they have all this data in their data lakes they can get to do all kinds of use cases on top of those they can do data science they can do machine learning they can even do real-time streaming with it so they're kept collecting this data into data lakes.

# The problem with Data Lakes:

Many of the projects are falling and what's happening is you could say garbage in garbage out.

**Messy data:** what happens if messy data enters the system? “Garbage” data is stored and it is impossible to extract needed or wanted value. How to fix this problem? You can create new Spark jobs to validate the data.

**Failed jobs:** Failed jobs leave data in a corrupt state. This requires tedious data cleanup after failed jobs.

**Mistakes and failure:** Even with validation jobs there is always room for error. You need to make sure that it is possible to reprocess part of the data if any error is found then we just simply delete corrupt data and start loading it again.

# Basic project architecture

Set of events that are coming into Kafka or Kinesis and you want to do a bunch of different things with it you want to do some streaming analytics you also want to do some kind of more intense AI and reporting on the historical data with a data lake.

![Flow](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/datalake.jpg?raw=true)

# Challenges while Designing

**Challenge No 1:** Historical Reporting

we can use apache spark it's going to read from Kafka and do streaming analytics. On historical reporting streaming is great it tells you what's happening right now.
> Problem?
 But it doesn't let me look back in time and do more complicated things like machine learning. 


**lambda architecture saves our life** what it means in addition to running the streaming pipeline that I use for kind of the immediate results I'm also going to run this spark batch pipeline to archive all this data into the data lake and do reporting and machine learning on it.


**Challenge No 2:** Messy Data

We have all the data in data lake which can be used by data scientists for machine learning, reporting and data modeling.

> Problem?
> data scientists are looking at my data Lake and telling me this data doesn't make any sense it's too messy usually problem with big data.

**Data validation save our life**  to fix this problem we just put validations into all spots in the pipeline now it's really important that we do it in both places because we're running two different pipelines here but again spark has unified API so it's not too hard so we'll add validations to both parts and remove the messy data.


**Challenge No 3:** Fixing Mistakes

We have put the validation in our pipelines to clear the messy data but it turns out before I put those validations in place some messy data leaked out.
> Problem?
some messy data leaked out in data lake. so now I need to figure out and it's hard when all you have is a distributed file system.

**Recompute save our life** we have to partition it by date and build a framework around spark that will allow me to recompute from any if anything goes wrong I'll just blow that whole folder away and recompute it from scratch and by reprocessing fix the mistakes that happened through the leak 


**Challenge No 4:** Updates in Data
Now we have clear data in the data lake. The next request is we have to go through this data Lake and remove/update all of these customer addresses but keep everything else.

> Problem?
 so now I have to worry about updates, can you even do that in the data Lake.

**Update framework save our life** So I'll build another spark job and it will read that data in update/remove it and write it back out. it doesn't crash in the middle because of huge data. you don't want to run this thing at the wrong time because if somebody is querying the data lake while I'm modifying it they'll see inconsistent results.


**Great! So now we understand the main problems that delta lake is there to address. And by solving these problems, they also provide some additional capabilities out of the box. We will learn more about delta lake in the next blog and try to understand how delta lake address all these problems. See you in the next blog.**
