---
title: "From Spark to DuckDB + Delta Lake: The Next Evolution"
layout: post
excerpt: "The data landscape is rapidly evolving, with new tools emerging to enhance efficiency and reduce costs."
last_modified_at: 2024-06-30T12:10:01-05:00
tags:
  - DuckDB 
  - Cost
  - Delta Lake
  - Spark 
  - Python
  - SQL
  - Big Data
  - Embedded
---

# DuckDB Introduction

DuckDB is an in-process SQL OLAP (Online Analytical Processing) database management system designed to execute rapid analytical queries on large datasets. Known for its robust and high-performance capabilities.

 - **Free and Open Source**: DuckDB is available at no cost and its source code is open for anyone to view, modify, and distribute
 - **In-process** signifies that the DBMS features operate directly within the application you're using, rather than as an external process that your application connects. 
 - **OLAP** denotes databases optimized for data analysis. DuckDB has become a popular choice among data analysts
 - **Embedded**: DuckDB runs within the application it serves, rather than as a separate, standalone process.


## DuckDB Use Cases

 1. **Data Integration and ETL**: As discussed earlier, DuckDB supports ETL processes, making it useful for integrating data from multiple sources, transforming it, and loading it into a database for further analysis or reporting.
 2. **Analytics and Business Intelligence**: DuckDB’s columnar storage and vectorized query execution make it well-suited for analytical queries on large datasets.
 3. **Embedded Applications**: Being designed for embedding into applications, DuckDB is ideal for scenarios where a lightweight, self-contained database is needed within the application itself.
 4. **Foreign Data Processing Without Copying**: DuckDB can process foreign data directly without the need for copying. For instance, the DuckDB Python package allows you to run queries directly on Pandas data without importing or duplicating any data.
 5. **Real-time Applications**: In applications requiring real-time data processing or low-latency responses, DuckDB’s efficient query execution and concurrency support can be advantageous.

# Spark Introduction
Apache Spark is an open-source, distributed computing system designed for big data processing and analytics.  Spark is known for its speed, ease of use, and sophisticated analytics capabilities, including support for SQL, streaming data, machine learning, and graph processing.

# Spark addressed a gap that might be no longer exists today
Apache Spark initial release **May 26, 2014**. The foundation of Spark was built on Resilient Distributed Datasets (RDDs), a distributed memory abstraction that lets programmers perform in-memory computations on large clusters in a fault-tolerant manner." There was a significant need for performing large-scale in-memory computations across multiple machines, as individual machines had limited RAM.

But honestly, does that gap still exist? Nowadays, we collectively source our infrastructure in the cloud. And exploring cloud options can be quite satisfying.

| EC2 Instance Type | vCPU | RAM (GiB) | Date  |
|-------------------|------|-----------|-------|
| r3.8xlarge        | 32   | 244       | 2014  |
| u-24tb1.metal     | 448  | 24,576    | 2024  |


## Most companies don’t have big data

Spark excels at processing terabytes of data through distributed computation across multiple nodes. However, this distributed coordination can introduce considerable overhead when handling small and medium-sized datasets (10–100 GB). I've observed, approximately 60% involve small jobs, 30% medium-sized jobs, and perhaps 10% require the heavy lifting job capabilities of Spark.

Spark has evolved far beyond RDDs. Today, it offers capabilities in streaming, machine learning, and SQL processing, making it a comprehensive toolkit. Many data engineers admire Spark for its versatility. However, when tasked solely with writing ETL jobs or constructing a data lake, are we fully utilizing Spark's broader feature set?

> We might have some data that doesn't need Spark or Databricks, but for the sake of use to architecture, we run everything on Databricks or pySpark. Why not? We have the budget, we're short on time, and we prefer to keep things simple.

> Do we need a complex distributed system like Spark for handling data processing if datasets fit on just a single machine?

# The DuckDB

## DuckDB + Python API
DuckDB's Python API allows for seamless integration with Python applications, enabling data scientists and engineers to leverage its powerful SQL capabilities directly within their Python scripts. 

DuckDB's efficient execution engine can often replace simple and medium Spark jobs, offering a more lightweight and faster alternative for many common data processing tasks, thus streamlining the workflow and reducing resource consumption.

[# Billion of Rows Benchmark with DuckDB (450GB)](https://towardsdatascience.com/my-first-billion-of-rows-in-duckdb-11873e5edbb5)

```python
import duckdb

# Connect to an in-memory DuckDB instance
with duckdb.connect() as con:

	con.execute("CREATE TABLE sample1 AS SELECT * FROM read_csv_auto('sample_data1.csv')")
	con.execute("CREATE TABLE sample2 AS SELECT * FROM read_csv_auto('sample_data2.csv')")
	con.execute("CREATE TABLE selected_data AS SELECT id, category, value FROM sample1")

	# Aggregate data
	con.execute("""
		CREATE TABLE aggregated_data AS
		SELECT category, SUM(value) AS total_value
		FROM selected_data
		GROUP BY category
	""")

	# Filter records
	con.execute("""
		CREATE TABLE filtered_data AS
		SELECT * FROM aggregated_data
		WHERE total_value > 30
	""")

	# Join with another table
	con.execute("""
		CREATE TABLE final_result AS
		SELECT f.category, f.total_value, s.description
		FROM filtered_data f
		JOIN sample2 s
		ON f.category = s.category
	""")
	# Write to parquet file
	db.sql("COPY (SELECT * FROM final_result) TO 'sample.parquet'")


```

## DuckDB + Spark API

What makes DuckDB interesting is its new compatibility with the Spark API. Known for its high performance and ease of use, DuckDB now provides an interface that mimics the Spark API. This allows developers to leverage their existing knowledge and codebase, enabling data engineers familiar with Spark to seamlessly transition to using DuckDB without a steep learning curve.

The Spark API compatibility enables DuckDB to integrate smoothly into existing ETL pipelines and workflows that are built around Spark. This compatibility provides a powerful combination: the efficiency and simplicity of DuckDB with the flexibility and robustness of Spark. It also allows for easier adoption of DuckDB in environments where Spark is already established, offering a way to optimize performance for certain tasks without abandoning familiar tools and paradigms.

> DuckDB’s Python client offers a Spark-compatible API. The API aims to be fully compatible with the [PySpark API](https://spark.apache.org/docs/3.5.0/api/python/reference/index.html), allowing you to use the familiar Spark API. All statements are translated to DuckDB’s internal plans using our [relationalAPI](https://duckdb.org/docs/api/python/relational_api) and executed using DuckDB’s query engine

```python
import os

# Read the environment variable
use_duckdb = os.getenv("USE_DUCKDB", "false").lower() == "true"

if use_duckdb:
    # check current supported functions at https://github.com/duckdb/duckdb/blob/main/tools/pythonpkg/duckdb/experimental/spark/sql/functions.py
    from duckdb.experimental.spark.sql.functions import avg, col, count
    from duckdb.experimental.spark.sql import SparkSession
else:
    from pyspark.sql.functions import avg, col, count
    from pyspark.sql import SparkSession

# create a SparkSession
spark = SparkSession.builder.appName("HackerNewsAuthorStats").getOrCreate()

df = spark.read.parquet("/data/hacker_news_2021_2022.parquet")

# Does users who post more stories tend to have higher or lower average scores ?
result = (
    df.filter((col("type") == "story") & (col("by") != "NULL"))
    .groupBy(col("by"))
    .agg(
        avg(col("score")).alias("average_score"),
        count(col("id")).alias("number_of_stories"),
    )
    .filter(col("number_of_stories") > 1)  # Filter users with more than one story
    .orderBy(
        col("number_of_stories").desc(), col("average_score").desc()
    )  # Order by the number of stories first, then by average score
    .limit(10)
)

# show the result
result.show()
```

## DuckDB + DeltaLake API


### Introduction
DuckDB now supports Delta Lake natively, combining the strengths of DuckDB's analytical capabilities with Delta Lake's robust storage framework. This integration aims to provide a seamless and efficient experience for users needing advanced data management features.

### Writing/Creating Delta Tables

To create and query Delta tables in DuckDB, you need to install the necessary packages and set up your data environment:

```python
pip install duckdb pandas deltalake

import duckdb
from deltalake import DeltaTable, write_deltalake

with  duckdb.connect() as  con:
	df1 = con.query("SELECT i AS id, i % 2 AS part, 'value-' || i AS value FROM range(0, 5) tbl(i)").df()
	df2 = con.query("SELECT i AS id, i % 2 AS part, 'value-' || i AS value FROM range(5, 10) tbl(i)").df()
	write_deltalake(f"./my_delta_table", df1, partition_by=["part"])
	write_deltalake(f"./my_delta_table", df2, partition_by=["part"], mode='append')

```
###  Reading/Querying Delta Tables

```python
import duckdb
from deltalake import DeltaTable, write_deltalake

with  duckdb.connect() as  db:
	db.install_extension('delta')
	db.load_extension('delta')
	data=db.sql("select * from delta_scan('./my_delta_table')")
	data.show()
```

The [duckdb_delta](https://github.com/duckdb/duckdb_delta) extension adds support for the [Delta Lake open-source storage format](https://delta.io/). It is built using the [Delta Kernel](https://github.com/delta-incubator/delta-kernel-rs). The extension offers **read/write support** for delta tables, both local and remote.

# DuckDB offers significant potential

Many companies rely heavily on SQL, and DuckDB shows promise for cost savings by processing data on a single node. It’s essential to consider these new tools like DuckDB for certain workloads. Given that compute power equates to money, DuckDB could significantly reduce costs by taking over some processing tasks from Snowflake or Databricks.
