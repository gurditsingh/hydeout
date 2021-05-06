## What is File Format

A file format is the definition of how information is stored in HDFS. Hadoop does not have a default file format and the choice of a format depends on its use case. File format should be well-defined and expressive. It should be able to handle variety of data structures specifically structs, records, maps, arrays along with strings, numbers etc.

The big problem in the performance of applications that use HDFS such as MapReduce or Spark is the information search time and the writing time. Managing the processing and storage of large volumes of information is complex, in addition to other difficulties such as the evolution of storage schemes or restrictions.
<!--stackedit_data:
eyJoaXN0b3J5IjpbODA4NjUzMjM0LC0yMDg4NzQ2NjEyLC0yMD
g4NzQ2NjEyXX0=
-->