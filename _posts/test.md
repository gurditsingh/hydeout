## Need of File Formats

A file format is the definition of how information is stored in HDFS. Hadoop does not have a default file format and the choice of a format depends on its use case. File format should be well-defined and expressive. It should be able to handle variety of data structures specifically structs, records, maps, arrays along with strings, numbers etc.

The big problem in the performance of applications that use HDFS such as Spark is the time it takes to find relevant data in a particular location and the time it takes to write the data back to another location. Managing the processing and storage of large volumes of information is complex, in addition to other difficulties such as the evolution of storage schemes or restrictions. Along with the storage cost, processing the data comes with CPU, Network, IO costs, etc., As the data increases, the cost for processing and storage increases too.

Benefits of choosing an appropriate file format:
 - Faster read times
 - Faster write times
 - Splittable files
 - Schema evolution support
 - Advanced compression support
 


<!--stackedit_data:
eyJoaXN0b3J5IjpbOTUyOTQ5OTc0LC0xMTIzOTUwNzM2LC0yMD
g4NzQ2NjEyLC0yMDg4NzQ2NjEyXX0=
-->