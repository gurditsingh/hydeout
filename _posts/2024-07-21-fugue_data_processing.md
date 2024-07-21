---
title: "Seamless Data Processing with Fugue: Integrating Pandas, DuckDB, and Spark"
layout: post
excerpt: "Leverage Fugue to write unified code that adapts to different execution engines, enhancing efficiency and flexibility in your data workflows."
last_modified_at: 2024-07-21T10:11:03-05:00
tags:
  - DuckDB 
  - Fugue
  - Engines
  - Spark 
  - Python
  - SQL
  - Big Data
  - Pandas
---

# Data Processing Needs
In today's data-driven landscape, organizations face diverse data processing needs that demand flexible solutions. For smaller datasets requiring efficient, in-memory processing and quick query execution, DuckDB emerges as a robust choice. Meanwhile, for handling large-scale data operations with scalability and distributed computing capabilities, Spark provides a powerful solution.

# Seamless Integration: Fugue
Fugue bridges these tools seamlessly, enabling organizations to optimize their data processing workflows. Fugue's abstraction layer allows data professionals to switch between DuckDB and Spark without needing to rewrite code, ensuring that they can effectively manage data of varying scales and complexities with ease.

[Fugue](https://github.com/fugue-project/fugue), an open-source abstraction layer, provides a seamless transition from a single machine to a distributed computing setting. With Fugue, users can code their logic in native Python, Pandas, or SQL, and then bring it to the Spark, Dask, Ray and Duckdb.

![Fugue](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/fugue_arc.jpg?raw=true)



In the world of data processing, flexibility and scalability are key. Fugue, an abstraction layer for distributed computing, offers a unique solution by allowing users to seamlessly switch between different computing frameworks. Fugue can accelerate the development of big data projects by **decreasing compute costs and by increasing developer productivity.**

# Separating Logic from Execution

One of the significant challenges with using Python Pandas/SQL and Spark is the tight coupling between the logic and the interface. This inflexibility forces data engineer to make an early decision on the tool they'll use, often without knowing how their data needs might evolve. Here are two scenarios that highlight this problem:

1.  A data engineer starts with Python Pandas/SQL for its simplicity and efficiency with smaller datasets. However, as the dataset grows, Pandas struggles with performance, costly hardware upgrades to handle the increased load (vertical scaling).
2.  Conversely, a data engineer anticipates large data volumes and opts for Spark from the outset. If the data doesn't grow as expected, the project suffers from unnecessary complexity and slower performance due to Spark's overhead.

In both scenarios, the user ends up with a wrong tool for the job. These issues can be mitigated by separating logic from execution. Fugue serves as an effective abstraction layer, enabling users to write a single codebase that is compatible with both Python Pandas/SQL and Spark. At runtime, the appropriate execution engine can be selected, providing the flexibility to handle varying data sizes and processing needs efficiently.

# Supporting API and SQL Interface

Fugue provides robust support for both API and SQL interfaces, making it highly versatile for different user preferences and use cases. Whether you prefer writing data processing logic using an API in Python or through SQL queries.

## Fugue API
```python
import pandas as pd
from typing import Dict
from fugue import transform
import fugue.api as fa

input_df = pd.DataFrame({"id":[0,1,2], "value": (["A", "B", "C"])})
map_dict = {"A": "Apple", "B": "Banana", "C": "Carrot"}

def map_letter_to_food(df: pd.DataFrame, mapping: Dict[str, str]) -> pd.DataFrame:
    df["value"] = df["value"].map(mapping)
    return df

def run(engine=None):
    with fa.engine_context(engine):
        df = fa.load("/path/to/file.parquet")
        out = fa.transform(df, map_letter_to_food, schema="*")
        fa.save(out, "/path/to/output_file.parquet")

run()                 # runs on Pandas
run(engine="spark")   # runs on Spark
run(engine="dask")    # runs on Dask
```
## Fugue SQL
```python
from fugue.api import fugue_sql
import json
import pandas as pd
from typing import Dict
from fugue import transform


input_df = pd.DataFrame({"id":[0,1,2], "value": (["A", "B", "C"])})
map_dict = {"A": "Apple", "B": "Banana", "C": "Carrot"}

def map_letter_to_food(df: pd.DataFrame, mapping: Dict[str, str]) -> pd.DataFrame:
    df["value"] = df["value"].map(mapping)
    return df

query = """
 SELECT id, value
 FROM input_df
 TRANSFORM USING map_letter_to_food(mapping={{mapping}}) SCHEMA *
 """
map_dict_str = json.dumps(map_dict)

# returns Pandas DataFrame
fugue_sql(query,mapping=map_dict_str)

# returns Spark DataFrame
fugue_sql(query, mapping=map_dict_str, engine="spark")
```


# Leveraging Multiple Execution Engines
Fugue provides a unified interface that allows users to seamlessly switch between different execution engines, such as Pandas, DuckDB, and Spark.

## Fugue with Pandas
Fugue integrates seamlessly with Pandas, allowing users to leverage the simplicity and efficiency of Pandas for small to medium-sized datasets. 

    `%%fsql` takes the ExecutionEngine as a parameter: Pandas

```SQL
%%fsql pandas

cust = LOAD "/FileStore/tables/customer.parquet"
prod = LOAD "/FileStore/tables/product.parquet"

# Joining two dataset
SELECT p.ProductID,p.ProductCategory,p.ProductBrand,p.ProductPrice,c.CustomerAge,c.CustomerGender,c.PurchaseFrequency,c.CustomerSatisfaction,c.PurchaseIntent
FROM cust c INNER JOIN prod p
ON c.ProductID = p.ProductID

# Filtering the dataset
SELECT *
WHERE CustomerAge > 18 AND PurchaseFrequency > 10 AND CustomerSatisfaction > 3 AND PurchaseIntent = 1

# Cumulative Sum on the dataset
SELECT ProductCategory,ProductBrand,
SUM(ProductPrice) OVER (PARTITION BY ProductCategory ORDER BY ProductPrice ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS CumulativeSum

  

PRINT
``` 
## Fugue with DuckDB

Fugue integrates seamlessly with DuckDB, making it easy to handle small to medium-sized datasets efficiently.

    `%%fsql` takes the ExecutionEngine as a parameter: DuckDB

```SQL
%%fsql duckdb

cust = LOAD "/FileStore/tables/customer.parquet"
prod = LOAD "/FileStore/tables/product.parquet"

# Joining two dataset
SELECT p.ProductID,p.ProductCategory,p.ProductBrand,p.ProductPrice,c.CustomerAge,c.CustomerGender,c.PurchaseFrequency,c.CustomerSatisfaction,c.PurchaseIntent
FROM cust c INNER JOIN prod p
ON c.ProductID = p.ProductID

# Filtering the dataset
SELECT *
WHERE CustomerAge > 18 AND PurchaseFrequency > 10 AND CustomerSatisfaction > 3 AND PurchaseIntent = 1

# Cumulative Sum on the dataset
SELECT ProductCategory,ProductBrand,
SUM(ProductPrice) OVER (PARTITION BY ProductCategory ORDER BY ProductPrice ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS CumulativeSum

  

PRINT
``` 

## Fugue with Spark
Fugue integrates seamlessly with Spark, allowing users to harness the power of distributed computing for processing large datasets

    `%%fsql` takes the ExecutionEngine as a parameter: Spark

```SQL
%%fsql spark

cust = LOAD "/FileStore/tables/customer.parquet"
prod = LOAD "/FileStore/tables/product.parquet"

# Joining two dataset
SELECT p.ProductID,p.ProductCategory,p.ProductBrand,p.ProductPrice,c.CustomerAge,c.CustomerGender,c.PurchaseFrequency,c.CustomerSatisfaction,c.PurchaseIntent
FROM cust c INNER JOIN prod p
ON c.ProductID = p.ProductID

# Filtering the dataset
SELECT *
WHERE CustomerAge > 18 AND PurchaseFrequency > 10 AND CustomerSatisfaction > 3 AND PurchaseIntent = 1

# Cumulative Sum on the dataset
SELECT ProductCategory,ProductBrand,
SUM(ProductPrice) OVER (PARTITION BY ProductCategory ORDER BY ProductPrice ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS CumulativeSum

  

PRINT
``` 

# Speed Up Development Cycles and Testing in Big Data Projects
Testing code in Spark can be tedious and time-consuming. There are two common approaches for developing Spark applications.

 1. Databricks users often rely on the `databricks-connect` Python library, which substitutes the local PySpark installation. When PySpark is called, the execution plan is compiled locally and executed on the configured cluster, meaning even simple tests and code changes require spinning up the backend cluster, causing delays and incurring high costs.
 2. The second approach involves developing locally and then using the spark-submit tool to package the code and run it on the cluster via SSH. This method is also time-consuming and requires more effort. Even with local testing, Spark's startup time is slower compared to Pandas because of the JVM environment setup. Additionally, assertions on DataFrame operations necessitate either a collect() or toPandas() call, both of which are slower than Pandas-based evaluations.

**Fugue addresses** these challenges by allowing you to select an execution engine at runtime. During testing, you can use the Pandas-based or Duckdb engine on smaller data, and then switch to the Spark engine for production. This approach makes testing faster and cheaper because the Spark runtime doesn't need to be initiated for every code test. After local testing with Pandas or Duckdb, the same code can be scaled up using the Spark execution engine.

# Why Fugue?
With Fugue, developers can rapidly prototype in a scale-agnostic manner and identify errors more quickly, accelerating the development process. Additionally, Fugue offers several key benefits:

-   **Reduced Unit Testing**: Unit testing requirements are minimized, leading to less boilerplate code.
-   **Flexible Logic Expression**: Developers can write their logic in Python Pandas or Duckdb, according to their preference.
-   **Simplified Maintenance**: Maintaining Spark applications becomes more manageable.
-   **Reusable Functions**: Functions can be seamlessly reused across both Pandas, Duckdb and Spark projects.

## Reducing Compute Costs

By leveraging Fugue’s ability to switch seamlessly between Pandas, Duckdb and Spark execution engines, developers can prototype and test code locally before scaling up to a Spark cluster. This flexibility, which is not constrained by the PySpark API for defining logic, helps in reducing compute costs in two key ways:

-   **Local Unit Testing**: You can perform unit testing on a local machine before deploying code to Spark, reducing the need for extensive cluster resources during development.
-   **Fewer Cluster Errors**: More development and debugging can be done locally, leading to fewer costly mistakes on the cluster and minimizing expensive errors.
