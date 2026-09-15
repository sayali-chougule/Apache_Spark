# Parallel Programming using Resilient Distributed Datasets

## What are RDD

A resilient distributed dataset is
- Spark's primary data abstraction
- A fault-tolerant collection of elements
- Partitioned across the nodes of the cluster
- Capable of accepting parallel operations
- Immutable

## Spark Applications
- Consists of a *Driver Program* that runs 
    - the user's main functions
    - and multiple parallel operations on a cluster

## RDD supported files

#### Supported File types
- text
- SequenceFiles
- Avro
- Parquet
- Hadoop input formats

#### Supported File Formats
- Local
- Cassandra
- Hbase
- HDFS
- Amazon S3
- and others
- SQL and NoSQL
