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

## How data stored on Internally

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
The hybrid storage model is a combination of both the row-wise and the columnar-wise model. In this model, we first select the groups of rows that we intend to store.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTY2NzUxNjIsLTk1NjIyNDAxNiwtOD
Q0Njc1OTc0LC0xMzAwNDAyNjM0LC04NDIyNzAwNzYsMTkwMDk4
MzM1NiwtMTUxMDc0MzQ1MywxNTg1MjA1ODQzLC03NzM2NTAwNz
UsOTIxMDk5MjYzLDk1Mjk0OTk3NCwtMTEyMzk1MDczNiwtMjA4
ODc0NjYxMiwtMjA4ODc0NjYxMl19
-->