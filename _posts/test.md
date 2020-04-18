# Introduction

Big data is used by organisations for the sole purpose of analytics. However, before companies can set out to extract insights and valuable information from big data, they must have the knowledge of data sources. Data, as we know, is massive and exists in various forms. Therefore we can say that dealing with big data in the best possible manner is becoming the main area of interest for businesses, scientists and individuals. When processing large amounts of data, there is usually a delay between the point when data is collected and its availability in reports and dashboards. In this article we’ll try to explore data processing architectures that serve as the backbone of various enterprise applications known as Lambda Architecture.

# Lambda Architecture

The basis of the Lambda architecture is to compute arbitrary functions on distributed datasets in real-time and to combine batch and real-time processing capabilities to balance data latency throughput, and fault tolerance by using batch processing to provide comprehensive and accurate views of batch data, while simultaneously using real-time stream processing to provide views of online data.


While we mention data processing we basically use this term to represent high throughput, low latency and aiming for near-real-time applications. Which also would allow the developers to define delta rules in the form of code logic or NLP in event-based data processing models to achieve robustness, automation and improve the data quality.

**In this architecture**, one can query both fresh and historical data. To gain insight into the historical data movements. The architecture has also solved the problem of computation of arbitrary functions. In general, a problem can be segregated into three layers:

 - Batch Layer 
 - Speed Layer
 - Serving Layer

 
![Lambda Architecture](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/lambda.png?raw=true) 
 

 1. Batch Layer
 
	 The batch layer is mainly responsible for two tasks. The first is to store the constantly growing master data in a data lake, which is in this case a Hadoop distributed file system or databases such as in memory databases or NoSQL based storages. The second task is to precompute batch views for this distributed data by using the Spark or MapReduce processing paradigm. Those batch views can be used to answer incoming queries with low read latency.

 2. Batch Layer

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5NTQ3NTkzMSwtMTY2MjY0OTg3OCw0NT
g4OTQyNzYsLTE4MTYwNTc2OTcsLTUzMjAyMzQzOCwtMzA5MTIz
MDU2LDQ0MzA0NDU2NSwtMjUyNTk3MDE2XX0=
-->