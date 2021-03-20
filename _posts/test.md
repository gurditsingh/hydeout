
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

## Try to understand in steps
let's try to understand the traditional way we have been processing data and then let's see how we convert the whole thing into the modern way implementing modernized data solutions specifically in cloud or Microsoft services or what sort of azure services we use for implementing various parts of our data solution and at the end let's see how we can use azure synapse for implementing the same.

## Step 1: Traditional way

![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/old-way-DWH.jpg?raw=true)

 - First Layer we have multiple structured sources like standard OLTP databases, cloud databases, csv file, excel files and some of unstructured sources like logs messages, sensor data, json, avro etc. These all input sources can be loaded into the system.
 - Next Layer we create relational data warehouse. 
	 - To load the data into data warehouse we generally use ETL (Extract Transform Load). ETL load the structured data into the Relational DW and ETL/ELT we use Hadoop and Spark to load the structured or unstructured data into the Relational DW.
	 - Sometime to cater the end user (serving layer) requirements we might create another repository let's say it's a file share or it's just a folder that contains some set to raw data.
	 - Next we create cubes nowadays we call these cubes as enterprise models you can use various components for creating this enterprise model this is actually a multi-dimensional database which is an optimized data structure for performing analytics.
- Next Layer is serving layer basically of information consumers to consume the created data in the way of Relational DW or Modes.
	- users can get data based on their requirements so user can connect with the file share or the folder that have been created for storing raw data or they can get data from relational data warehouse as well can connect with relational data warehouse or the enterprise  model.


## Step 2: Modern way (by use Azure Cloud services)
In the below image we have highlighted cloud services which are segregated from first and last layer. 
![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/new-cloud-way-DWH.jpg?raw=true)

- First Layer we have multiple structured sources like standard OLTP databases, cloud databases, csv file, excel files and some of unstructured sources like logs messages, sensor data, json, avro etc. These all input sources can be loaded into the system.
 - Next Layer we create relational data warehouse by using Azure Cloud Services.
	 -  To load the data into data warehouse we generally use ETL (Extract Transform Load) like Azure Data Factory or SSIS package . ETL load the structured data into the Azure sql Data Warehouse (Relational DW).
	 -  ETL/ELT we use Azure HD insight for Hadoop and Spark or use Azure Databricks to load the structured or unstructured data into the  Azure sql Data Warehouse (Relational DW).
	 - 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzE1MzAyNzUyLDE4NzQ3OTEzNDIsLTk4ND
IxMzMxNywxNjMwMzI4ODUzLC0xNTk1MjkxNTYsLTEyMjYyODA4
ODcsLTE0Njk1MTIwMDgsLTE2OTU1MTA2OTUsMzAzNzgzMjYxLD
E0NTM4OTYwMTIsLTIwNTM3NTQ2MjcsLTIwOTYyMzg5OCwtODA0
NTU5MTE2LDU5ODU4MDkxNiwtNjAzMjA0OTQzLDMwOTE5NDAyMy
w5NjkyNjY3NDQsMTgzNzc0NDc4MCwtMTc3MjIyNTcwNCwtMTY5
NDA4MjU2XX0=
-->