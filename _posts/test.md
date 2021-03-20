
let's first try to understand what is **Data Warehouse** and **Data Lake** and understand will Data Lake & Enterprise Data Warehouse (EDW) coexist?

### Data Warehouse
Data Warehouse (DW) is process for collecting and managing data from varied sources to provide meaningful business insights. A Data warehouse is typically used to connect and analyze business data from heterogeneous sources.

In the early days of data repository, a **data warehouse** (**DW** or **DWH**), also known as an **enterprise data  warehouse** (**EDW**), is a commonly known system used for **reporting** and **data analysis** and is considered a core component of **business intelligence**, **Extract transform load** (ETL). They store current and historical data in one single place.

### Data Lake
A data lake is a centralized repository that allows you to store all your structured and unstructured data at any scale. You can store your data as-is, without having to first structure the data, and run different types of analytics from dashboards and visualizations to big data processing, real-time analytics, and machine learning to guide better decisions.

### Data Lakes compared to Data Warehouses:

![DLDW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/DataLake_DataWarehouse.jpg?raw=true)

### Data Lake & Data Warehouse coexist?
The answer is yes. We call this new emerging pattern as a **cloud lakehouse**, bringing the best of data warehouse and data lake altogether.

![lakehouse](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data-lakehouse.png?raw=true)

### What is a Cloud Lakehouse?
New systems are beginning to emerge that address the limitations of data lakes. A lakehouse is a new, open architecture that combines the best elements of data lakes and data warehouses. Lakehouses implementing similar data structures and data management features to those in a data warehouse, directly on the kind of low cost storage used for data lakes. Some highlighted **benefits** includes:

 - Schema enforcement and governance
 - Support for both structured and unstructured
 - Storage is decoupled from compute
 - End-to-end streaming
 - Transaction support
 - AI + BI support

## What is Azure Synapse Analytics?

Microsoft’s Azure Synapse Analytics service, which enables a similar lakehouse pattern. Azure Synapse Analytics service is the de-facto service for combining data warehousing and big data analytics. And the Azure Synapse Workspace is providing an unique experience by unifying various components into a common user friendly interface.

![synapse](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/azure-synapse.png?raw=true)

## First try to understand the Traditional way
let's try to understand the traditional way we have been processing data and then let's see how we uh convert the whole thing into the modern way implementing modernized data solutions specifically in cloud or Microsoft services or what sort of azure services we use for implementing various parts of our data solution and at the end let's see how we can use azure synapse for implementing the same.

![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/old-way-DWH.jpg?raw=true)

 - First Layer we have multiple sources like standard OLTP databases, cloud databases, csv file, excel files generally. These all input sources can be loaded into the system.
 - Next Layer we create relational data warehouse. To load the data into data warehouse we generally use ETL (Extract Transform Load).

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODI0NTYxMTUsLTk4NDIxMzMxNywxNj
MwMzI4ODUzLC0xNTk1MjkxNTYsLTEyMjYyODA4ODcsLTE0Njk1
MTIwMDgsLTE2OTU1MTA2OTUsMzAzNzgzMjYxLDE0NTM4OTYwMT
IsLTIwNTM3NTQ2MjcsLTgwNDU1OTExNiw1OTg1ODA5MTYsLTYw
MzIwNDk0MywzMDkxOTQwMjMsOTY5MjY2NzQ0LDE4Mzc3NDQ3OD
AsLTE3NzIyMjU3MDQsLTE2OTQwODI1NiwtMTYyMDY2NzMyNCwt
MjAyNjc5NTcxM119
-->