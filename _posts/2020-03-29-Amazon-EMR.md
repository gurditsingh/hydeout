---
title: "Apache Spark on Amazon EMR "
layout: post
excerpt: "This tutorial is for Spark developper’s who don’t have any knowledge on Amazon Web Services and want to learn an easy and quick way to run a Spark job on Amazon EMR."
last_modified_at: 2020-03-29T11:27:01-05:00
tags:
  - Spark
  - Amazon
  - EMR
  - S3
---
# Amazon EMR
Amazone EMR cluster provides a managed hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances.
We can also run other popular distributed frameworks such as apache Spark and HBase in EMR and interact with data in other AWS datastores such as Amaxon S3 and Amazon DynamoDB.

# Types of Nodes in EMR [Master Nodes, Core Nodes, Task Nodes]
**Master Node**
The master node manages the cluster and typically runs master components of distributed applications. For example, the master node runs the YARN ResourceManager service to manage resources for applications, as well as the HDFS NameNode service. It also tracks the status of jobs submitted to the cluster and monitors the health of the instance groups.

**Core Nodes**
Core nodes are managed by the master node. Core nodes run the Data Node daemon to coordinate data storage as part of the Hadoop Distributed File System (HDFS). They also run the Task Tracker daemon and perform other parallel computation tasks on data that installed applications require. For example, a core node runs YARN NodeManager daemons, Hadoop MapReduce tasks, and Spark executors.

**Task Nodes**
Task nodes are optional. You can use them to add power to perform parallel computation tasks on data, such as Hadoop MapReduce tasks and Spark executors. Task nodes don't run the Data Node daemon, nor do they store data in HDFS

Because Spot Instances are often used to run task nodes, Amazon EMR has default functionality for scheduling YARN jobs so that running jobs don’t fail when task nodes running on Spot Instances are terminated. Amazon EMR does this by allowing application master processes to run only on core nodes. The application master process controls running jobs and needs to stay alive for the life of the job.

# what is Spot Instances
A Spot Instance is an unused EC2 instance that is available for less than the On-Demand price. Because Spot Instances enable you to request unused EC2 instances at steep discounts.

Spot Instances are a cost-effective choice if you can be flexible about when your applications run and if your applications can be interrupted. For example, Spot Instances are well-suited for data analysis, batch jobs, background processing, and optional tasks.

**Master Node on a Spot Instance**
The master node controls and directs the cluster. When it terminates, the cluster ends, so you should only launch the master node as a Spot Instance if you are running a cluster where sudden termination is acceptable.

**Core Nodes on Spot Instances**
Core nodes process data and store information using HDFS. Terminating a core instance risks data loss. For this reason, you should only run core nodes on Spot Instances when partial HDFS data loss is tolerable.

**Task Nodes on Spot Instances**
The task nodes process data but do not hold persistent data in HDFS. If they terminate because the Spot price has risen above your maximum Spot price, no data is lost and the effect on your cluster is minimal.

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

**WHICH ONE TO USE:**

For Amazon EMR, both the s3:// and s3n:// URIs are associated with the EMR filesystem and are functionally interchangeable in the context of Amazon EMR. For consistency sake, however, it is recommended to use the s3:// URI in the context of Amazon EMR.

# HDFS and EMRFS
Amazon EMR and Hadoop typically use two or more of the following file systems when processing a cluster. HDFS and EMRFS are the two main file systems used with Amazon EMR.

| File System  |Prefix  | Description  |
| ------------ | ------------ | ------------ |
|  HDFS |  hdfs:// (or no prefix) | By default HDFS is used by the master and core nodes |
|  EMRFS |  s3:// | EMRFS is an implementation of the Hadoop file system used for reading and writing regular files from Amazon EMR directly to Amazon S3  |

# Things need to know while provisioning Amazon EMR
**What is VPC (Virtual Private Cloud):**
A VPC is a virtual network specific to you within AWS for you to hold all your AWS services. It is a logical data center in AWS and will have gateways, route tables, network access control lists (ACL), subnets and security groups.

**Why use a VPC?**
When you open up a service within a public cloud, it is effectively open to the world and can be at risk to attacks from the internet. In order to lock your instances down and secure them against attacks from the outside, you lock them within a VPC. The VPC restricts what sort of traffic, IP addresses and also the users that can access your instances.

This prevents unwanted guests accessing your resources and secures from attacks. Not all services require access to the internet, so those can be locked away safely within a private network. You can then expose only certain machines to the internet.

**The following are the key concepts for VPCs:**
- A virtual private cloud (VPC) is a virtual network dedicated to your AWS account.

- A subnet is a range of IP addresses in your VPC.

- A route table contains a set of rules, called routes, that are used to determine where network traffic is directed.

- An internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. It therefore imposes no availability risks or bandwidth constraints on your network traffic.

- A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.


# FINAL STEP

# Lets Run a Spark job within Amazon EMR
This tutorial is for Spark developpers who dont have any knowledge on Amazon Web Services and want to learn an easy and quick way to run a Spark job on Amazon EMR.
please use the link to provision EMR : [Amazon EMR](https://medium.com/@lllsong/create-emr-and-run-spark-zeppelin-notebook-on-aws-ce7084e46045 "Amazon EMR")




