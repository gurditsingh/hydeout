---
title: "Apache Spark on Amazon EMR "
layout: post
excerpt: "Similar to Apache Hadoop, Spark is an open-source, distributed processing system commonly used for big data workloads. ... You can install Spark on an EMR cluster along with other Hadoop applications, and it can also leverage the EMR file system (EMRFS) to directly access data in Amazon S3."
last_modified_at: 2019-07-24T10:27:01-05:00
tags:
  - Spark
  - Amazon
  - EMR
  - S3
---

# Amazon EMR
Amazone EMR cluster provides a managed hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances.
We can also run other popular distributed frameworks such as apache Spark and HBase in EMR and interact with data in other AWS datastores such as Amaxon S3 and Amazon DynamoDB.

# S3(Amazon Simple Storage Service)
we are going to run out Spark applcation on top fo the Hadoop cluster, and we will put the input data source into the S3.

S3 is a distributed storage system and AWS's equivalent to HDFS.

We want to make sure that
- Our data is coming from some distributed file system that can be accessed by every node on our spark cluster
- Our spark application doesn't assume that our input data sits somewhere on our local disk because that will not scale.

By saving out input data source into S3,each spark node deployed on the EMR cluster can read the input data source from S3.


# Technically what is the difference between s3n, s3a and s3
**S3N (URI scheme: s3n) -** A native filesystem for reading and writing regular files on S3. S3N allows Hadoop to access files on S3 that were written with other tools, and conversely, other tools can access files written to S3N using Hadoop. S3N is stable and widely used, but it is not being updated with any new features.

**S3A (URI scheme: s3a) -** Hadoop’s successor to the S3N filesystem. S3A uses Amazon’s libraries to interact with S3. S3A supports accessing files larger than 5 GB, and it provides performance enhancements and other improvements. For Apache Hadoop, S3A is the successor to S3N and is backward compatible with S3N. Using Apache Hadoop, all objects accessible from s3n:// URLs should also be accessible from S3A by replacing the URL scheme.
Note
Amazon EMR does not currently support use of the Apache Hadoop S3A file system.

**S3 (URI scheme: s3) -** Apache Hadoop implementation of a block-based filesystem backed by S3. Apache Hadoop has deprecated use of this filesystem as of May 2016.

**Which one to use:**
For Amazon EMR, both the s3:// and s3n:// URIs are associated with the EMR filesystem and are functionally interchangeable in the context of Amazon EMR. For consistency sake, however, it is recommended to use the s3:// URI in the context of Amazon EMR.

# HDFS and EMRFS
Amazon EMR and Hadoop typically use two or more of the following file systems when processing a cluster. HDFS and EMRFS are the two main file systems used with Amazon EMR.

| File System  |Prefix  | Description  |
| ------------ | ------------ | ------------ |
|  HDFS |  hdfs:// (or no prefix) | By default HDFS is used by the master and core nodes |
|  EMRFS |  s3:// | EMRFS is an implementation of the Hadoop file system used for reading and writing regular files from Amazon EMR directly to Amazon S3  |


