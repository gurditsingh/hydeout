## What is Delta Lake?

In the past there are different storage solutions build to solve the common problem of data quality. Many architecture/tools are build to solve the problem. These tools provides many benefits like decoupling the business logic from storage and compute. It means user can scale the compute and storage power up and down but in between this data reliability lost. To provide the data reliability and quality  Delta Lake come into the picture.

Delta Lake is a file-based, open-source storage format that provides ACID transactions, scalable metadata handling, and unifies streaming and batch data processing. It runs on top of your existing data lakes and is compatible with Apache Spark and other processing engines. Delta Lake combine the both worlds OLAP(Online Analytical Processing) and OLTP(Online Transactional Processing) with the horizontal scalability of data lakes.

 - **ACID transactions :** It is really important that the data integrity is maintained in data lake means no more partial or corrupted data. Delta Lake ensures that all data changes written to storage are committed for durability and made visible to readers atomically.
 - **Unified Batch and Stream Processing :** In a Data lake, if we have an use case of both Stream processing and Batch processing it is normal to follow _Lamdba architecture_. But Delta Lake table has the ability to work both in batch and as a streaming source and sink all just work out of the box.
 - **Scalable data and metadata handling :** Delta Lake is built on data lakes, all reads and writes using Spark or other distributed processing engines are inherently scalable to petabyte-scale. However, unlike most other storage formats and query engines, Delta Lake leverages Spark to scale out all the metadata processing, thus efficiently handling metadata of bil‐ lions of files for petabyte-scale tables.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDM3NzYyNDk3LDMxMTE4NjY0OCwtNzgyMD
Y0MjUwLC0yMDg4NzQ2NjEyLC0zMzI0NTUzNjNdfQ==
-->