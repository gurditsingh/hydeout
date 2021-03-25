
## Azure Synapse

Azure Synapse Analytics is a limitless analytics service that brings together data integration, enterprise data warehousing and big data analytics. It gives you the freedom to query data on your terms, using either serverless or dedicated resources—at scale. Azure Synapse brings these worlds together with a unified experience to ingest, explore, prepare, manage and serve data for immediate BI and machine learning needs.

![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/synapse-unified-platform.png?raw=true)

 - **Azure Synapse Studio :** This tool is a web-based tool that provides developers to work with every aspect of Synapse Analytics from a single console. In this generally starts with creating a workspace and launching this tool that provides access to different synapse features like Ingesting data using import mechanisms or data pipelines and create data flows, explore data using notebooks, analyze data with spark jobs or SQL scripts, and finally visualize data for reporting and dashboarding purposes.
 - **Azure Synapse Data Integration :** This service comes with an integrated orchestration engine that is identical to Azure Data Factory to create data pipelines and rich data transformation capabilities within the Synapse workspace itself. Key features include support for 90+ data sources that include Azure-based data sources, open-source and cross-cloud data warehouses and databases, file-based data sources, No SQL based data sources, etc.
 - **Synapse SQL Pools :** This feature of the service available in a provisioned manner where a fixed capacity of DWU units is allocated to the instance of the service for data processing. Data can be imported into Synapse using different mechanisms like SSIS, Polybase, Azure Data Factory, etc.

	Synapse SQL feature is also available in a serverless manner, where no fixed capacity of the infrastructure needs to be provisioned. Instead, Azure manages the required infrastructure capacity to meet the needs of the workloads.
- **Apache Spark for Azure Synapse :** This component of Synapse provides Spark runtime to perform the same set of tasks like data loading, data processing, data preparation, ETLs, and other tasks that are generally related to data warehousing. Once a Synapse workspace is created, one can provision Apache Spark pools. Azure provides Data Bricks, too, as a service that is based on Spark runtime with a certain set of optimizations.

## Azure Synapse Architecture

In the below diagram gives you a high level overview of what is involved in this new in workspace environment and if we look at this everything's under a workspace an azure Synapse workspace you can create multiple workspaces. The main thing you'll be using is azure synapse studio and this is the new product that creates that single place where everything going to be used  underneath that azure synapse studio.

![DW](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/Azure-Synapse-Analytics.jpg?raw=true)

### Ingest Layer
At the top level have Ingest data Layer into synapse studio and it's using azure data factory. we don't call it data factory within synapse studio but we have pipelines and data flows to ingest the data and land the data in storage.

### Storage Layer
In the storage layer we have different options to load or store the data.

 - **Relational Database** you can land it into your traditional relational database or your data warehouse and that is what we used to call the sql data warehouse it's the same concept it's a relational database for your data warehouse.
 - **Data Lake** you can land it into your data lake store gen 2 it's your data lake (data lake store gen 2 is our c is our enhancement to) or what we used to call blob store what we still call blob store and azure data lake store we now call gen 1 we took the best features of both those products and put it into gen 2. so that's your landing zone it's schema on read it's like a file folder it's a glorified file structure now and i can land data in there in any type of format on that

## Next ?

Planning to create multiple blogs episodes on azure synapse covering various areas related to azure synapse and showing you the way of using these services for implementing your data warehouse solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NjUxODE0OTAsLTI5NzM3NjQxNSwxMT
E2MDEyNzY5LC02MTgxNDc5OTYsLTE5MjAxNDg4NDUsLTUxNjM2
NDc4MiwxODg5ODA1MTQxLDE1MzQ5Nzg4NDIsNzE1MTY0NzAzLD
E2NjY5NjA5MTgsLTIxMDEwNTY3LC03MTE3MDgzNjEsLTM5Njcx
NzI4Niw2ODU1MzA3OTEsNzE1MzAyNzUyLDE4NzQ3OTEzNDIsLT
k4NDIxMzMxNywxNjMwMzI4ODUzLC0xNTk1MjkxNTYsLTEyMjYy
ODA4ODddfQ==
-->