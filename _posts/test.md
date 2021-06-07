## What is Delta Lake?

In the past there are different storage solutions build to solve the common problem of data quality. Many architecture/tools are build to solve the problem. These tools provides many benefits like decoupling the business logic from storage and compute. It means user can scale the compute and storage power up and down but in between this data reliability lost. To provide the data reliability and quality  Delta Lake come into the picture.

Delta Lake is a file-based, open-source storage format that provides ACID transactions, scalable metadata handling, and unifies streaming and batch data processing. It runs on top of your existing data lakes and is compatible with Apache Spark and other processing engines. Delta Lake combine the both worlds OLAP(Online Analytical Processing) and OLTP(Online Transactional Processing) with the horizontal scalability of data lakes.

 - **ACID transactions :** It is really important that the data integrity is maintained in data lake means no more partial or corrupted data. Delta Lake ensures that all data changes written to storage are committed for durability and made visible to readers atomically.
 - **Unified Batch and Stream Processing :** In a Data lake, if we have an use case of both Stream processing and Batch processing it is normal to follow _Lamdba architecture_. But Delta Lake table has the ability to work both in batch and as a streaming source and sink all just work out of the box.
 - **Scalable data and metadata handling :** Delta Lake is built on data lakes, all reads and writes using Spark or other distributed processing engines are inherently scalable to petabyte-scale. Delta Lake leverages Spark to scale out all the metadata processing to handle metadata or large tables.
 - **Time Travel :** The Delta Lake transaction log records details about every change made to data providing a full audit trail of the changes. Data in the data lake will be versioned and snapshots are provided so that you can query them as if that snapshot was the current state of the system. This helps us to revert to older versions of our data lake for Audits, rollbacks and etc.
 - **Schema Enforcement :** Delta Lake automatically prevents the insertion of data with an incorrect schema, i.e. not matching the table schema. It prevents data corruption by preventing the bad data get into the system.
 - **Support for updates, merge and deletes :** Delta Lake supports merge, delete , and update operations to do complex operations. Most of the distributed processing frameworks do not support atomic data modification operations on data lakes.

## How to start with Delta Lake

 - **Databricks Community Edition :** The Databricks Community Edition is the free version of our cloud-based big data platform. Users can access a micro-cluster as well as a cluster manager and notebook environment. You can start with the Databricks environment in which the delta lake packages are pre-installed. 
 - **Set up project :** If you want to build a project using Delta Lake binaries from Maven Central Repository, you can use the following Maven coordinates.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTUwNTQzOTA2LDMxMTE4NjY0OCwtNzgyMD
Y0MjUwLC0yMDg4NzQ2NjEyLC0zMzI0NTUzNjNdfQ==
-->