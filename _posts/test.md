
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

![DLDW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/data-lakehouse.png?raw=true)

### What is a Cloud Lakehouse?
New systems are beginning to emerge that address the limitations of data lakes. A lakehouse is a new, open architecture that combines the best elements of data lakes and data warehouses. Lakehouses implementing similar data structures and data management features to those in a data warehouse, directly on the kind of low cost storage used for data lakes. Some highlighted **benefits** includes:

 - Schema enforcement and governance
 - Support for both structured and unstructured
 - Storage is decoupled from compute
 - End-to-end streaming
 - Transaction support
 - AI + BI support

## What is Azure Synapse Analytics?

Microsoft’s Azure Synapse Analytics service, which enables a similar lakehouse pattern. Azure Synapse Analytics service is the de-facto service for combining data warehousing and big data analytics.

Azure Synapse Analytics has combined a couple different technologies here:

 - **Azure Data Lake Storage** we have Azure Data Lake Storage, and Azure Data Lake Storage allows you to store a lot of different data types inside of one location or lake.
 - **Azure SQL Data Warehouse** 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0Njk1MTIwMDgsLTE2OTU1MTA2OTUsMz
AzNzgzMjYxLDE0NTM4OTYwMTIsLTIwNTM3NTQ2MjcsLTgwNDU1
OTExNiw1OTg1ODA5MTYsLTYwMzIwNDk0MywzMDkxOTQwMjMsOT
Y5MjY2NzQ0LDE4Mzc3NDQ3ODAsLTE3NzIyMjU3MDQsLTE2OTQw
ODI1NiwtMTYyMDY2NzMyNCwtMjAyNjc5NTcxMywtMTY4OTkwOD
k1Miw0ODI3NjMyMCwxMTgxMzE2NDEsLTE5MjcyNTc4NzAsMTYx
MTEwNDEwNV19
-->