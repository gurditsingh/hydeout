## Need of File Formats

A file format is the definition of how information is stored in HDFS. Hadoop does not have a default file format and the choice of a format depends on its use case. File format should be well-defined and expressive. It should be able to handle variety of data structures specifically structs, records, maps, arrays along with strings, numbers etc.

The big problem in the performance of applications that use HDFS such as Spark is the time it takes to find relevant data in a particular location and the time it takes to write the data back to another location. Managing the processing and storage of large volumes of information is complex, in addition to other difficulties such as the evolution of storage schemes or restrictions. Along with the storage cost, processing the data comes with CPU, Network, IO costs, etc., As the data increases, the cost for processing and storage increases too.

Benefits of choosing an appropriate file format:
 - Faster read times
 - Faster write times
 - Splittable files
 - Schema evolution support
 - Advanced compression support
 
 

## Different types of file formats
Some file formats are designed for general use, others are designed for more specific use cases, and some are designed with specific data characteristics in mind. So there really is quite a lot of  user choice.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_ep4_fileformats_types.png?raw=true)

 - **Unstructured :** The text files like CSV, TSV are mostly unstructured because text files are raw data and may contain more and less fields. But text files are also come under structured data as well.
 - **Semi-Structured :** The semi structured data may contains different fields per row and different kinds of fields. Semi structured data that contains tags or markers as an semantic elements, but they aren't as rigid as structured data. Typical examples of semi-structured data are XML and JSON.
 - **Structured :** Structured data formats, rigidly enforce schema and data type rules. Many leverages this knowledge about the data to provide optimizations at query time right out of the box. Typical examples of structured data are Apache Avro, Apache ORC and Apache Parquet.

## Physical Layout of file formats

### 1. Row oriented Storage
Row oriented databases are databases that organize data by record, keeping all of the data associated with a record next to each other in memory. A row wise stored methodology, rows are stored contiguously on disk. The data stored one after another inside of block. This type of storage methodology can be great if your goal is to access full rows at a time.

In a row store, or row oriented database, the data is stored row by row, such that the first column of a row will be next to the last column of the previous row. This allows the database write a row quickly because, all that needs to be done to write to it is to tack on another row to the end of the data.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_ep4_rowwise.png?raw=true)

**Challenges in Row Oriented Storage:** 

 - if you want to read data from third row of data, A2, B2, C2 is a pretty trivial operation in the row oriented model.
 - if you want to reconstruct the second column then this would require a linear scan of the entire data set.
 - if you want to update the second column values then this model would read the whole data that we don't require for the operation.
 - if you want to do aggregation then it brings extra data (columns) into memory which is slower than only selecting the columns that you are performing the aggregation on it.

### 2. Column oriented Storage
In a C-Store, columnar, or Column-oriented database, the data is stored column wise such that each row of a column will be next to other rows from that same column. In the columnar storage methodology, columns are stored contiguously On-disk. These types of Storage are read optimized.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_ep4_columnwise.png?raw=true)

**Challenges in Row Oriented Storage:** 

 - if you want to add a new row then it become the fairly intensive process.
 - if you have a workflow which requires heavy write then this model become a lot more expensive.
 - Most of the column wise models are not ACID compliance.

### 3. Hybrid Storage
The hybrid storage model is a combination of both the row-wise and the columnar-wise model. In this model, we first select the groups of rows that we intend to store. In this model we create row groups and we will apply the columnar layout inside each of the row groups. In this we've logically grouped together the rows of the table with the help of columnar partitioning scheme inside of the group.

![Spark](https://github.com/gurditsingh/blog/blob/gh-pages/_screenshots/spark_ep4_hybrid.png?raw=true)

## Types of Workflows

### OLTP(Online Transaction Processing Workflow)
An OLTP system captures and maintains transaction data. Each transaction involves individual data records made up of multiple fields or columns. Examples include banking and credit card activity or retail checkout scanning. In OLTP, the emphasis is on fast processing, because OLTP databases are read, written, and updated frequently. If a transaction fails, built-in system logic ensures data integrity.

 - It operates with short lived transactions or queries.
 - More processing focused rather than analysis focused.
 - It focused towards row based processing rather than column based processing.
 - In this data is generally updated and deleted on a per record basis or transaction basis.
 - It is Normalized workflow for efficiency.
 
 ### OLAP(Online Analytical Processing Workflow)
 OLAP applies complex queries to large amounts of historical data, aggregated from OLTP databases and other sources, for data mining, analytics, and business intelligence projects. In OLAP, the emphasis is on response time to these complex queries. Each query involves one or more columns of data aggregated from many rows.
 - These are generally workflows that involve column based analytics.
 - It operates with the more complex queries.
 - These types of workflows are best stored by columnar storage formats.
 - Handles large volumes of data with complex queries
 

## Let's examine the different file formats

### 1. CSV
It is a **Row-based format** and CSV files (comma-separated values) are usually used to exchange tabular data between systems using plain text. CSV is a row-based file format, which means that each row of the file is a row in the table. Essentially, CSV contains a header row that contains column names for the data, otherwise, files are considered partially structured. CSV files may not initially contain hierarchical or relational data. Data connections are usually established using multiple CSV files. Foreign keys are stored in columns of one or more files, but connections between these files are not expressed by the format itself.

 - Flexible
 - Row-based
 - Human Readable
 - Compressible
 - Splittable
 - Fast write

### 2. JSON
It is a **Row-based format** and JSON (JavaScript object notation) data are presented as key-value pairs in a partially structured format. JSON is often compared to XML because it can store data in a hierarchical format. Both formats are user-readable, but JSON documents are typically much smaller than XML.

 - Self describing schema
 - Row-based
 - Compressible
 - Splittable
 - Supports complex type
 - Supports hierarchical structures

### 3. Avro
It is a **Row-based format** that has a high degree of splitting. It is also described as a data serialization system similar to Java Serialization. The schema is stored in JSON format, while the data is stored in _binary format_, which minimizes file size and maximizes efficiency. Avro has reliable support for schema evolution by managing added, missing, and changed fields. Since Avro is a row-based format, it is the preferred format for handling large amounts of records as it is easy to add new rows.

 - Data format and Data Serialization
 - Schema stored in a file header
 - Row-based
 - binary format
 - Compressible
 - Splittable
 - Supports complex type

### 4. ORC
It is a **Hybrid based format** and ORC(Optimized Row Columnar) file format provides a highly efficient way to store data. It was designed to overcome the limitations of other file formats. It ideally stores data compact and enables skipping over irrelevant parts without the need for large, complex, or manually maintained indices.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MTcxMDUxNjYsLTU2NzgxMDc0NiwxMz
MwMTExNzUsLTE2NTgxNzg4MzgsMTg1MTIyODg0MywxMTg1NjE0
OTU5LC05NTYyMjQwMTYsLTg0NDY3NTk3NCwtMTMwMDQwMjYzNC
wtODQyMjcwMDc2LDE5MDA5ODMzNTYsLTE1MTA3NDM0NTMsMTU4
NTIwNTg0MywtNzczNjUwMDc1LDkyMTA5OTI2Myw5NTI5NDk5Nz
QsLTExMjM5NTA3MzYsLTIwODg3NDY2MTIsLTIwODg3NDY2MTJd
fQ==
-->