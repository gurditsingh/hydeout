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
