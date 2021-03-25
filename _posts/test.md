
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
At the top level you can ingest data into synapse studio it's it's a synapse analytics and it's using azure data factories they're familiar with aggregated factors you'll see in a demo it's the same thing and we don't call it data factory within it but we have pipelines and data flows is what we is what we use and that ingest part will land the data in storage 

## Next ?

Planning to create multiple blogs episodes on azure synapse covering various areas related to azure synapse and showing you the way of using these services for implementing your data warehouse solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTg1NTExODIzLC0yOTczNzY0MTUsMTExNj
AxMjc2OSwtNjE4MTQ3OTk2LC0xOTIwMTQ4ODQ1LC01MTYzNjQ3
ODIsMTg4OTgwNTE0MSwxNTM0OTc4ODQyLDcxNTE2NDcwMywxNj
Y2OTYwOTE4LC0yMTAxMDU2NywtNzExNzA4MzYxLC0zOTY3MTcy
ODYsNjg1NTMwNzkxLDcxNTMwMjc1MiwxODc0NzkxMzQyLC05OD
QyMTMzMTcsMTYzMDMyODg1MywtMTU5NTI5MTU2LC0xMjI2Mjgw
ODg3XX0=
-->