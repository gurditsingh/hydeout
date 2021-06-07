## What is Delta Lake?

In the past there are different storage solutions build to solve the common problem of data quality. Many architecture/tools are build to solve the problem. These tools provides many benefits like decoupling the business logic from storage and compute. It means user can scale the compute and storage power up and down but in between this data reliability lost. To provide the data reliability and quality  Delta Lake come into the picture.

Delta Lake is a file-based, open-source storage format that provides ACID transactions, scalable metadata handling, and unifies streaming and batch data processing. It runs on top of your existing data lakes and is compatible with Apache Spark and other processing engines. Delta Lake combine the both worlds OLAP(Online Analytical Processing) and OLTP(Online Transactional Processing) with the horizontal scalability of data lakes.

**ACID transactions**
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzc3ODU5MDk3LC03ODIwNjQyNTAsLTIwOD
g3NDY2MTIsLTMzMjQ1NTM2M119
-->