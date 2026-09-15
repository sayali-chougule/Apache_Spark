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


## Creating an RDD in Spark

1. Use an external or local file from Hadoop-supported file system such as 
    - HDFS
    - Cassandra
    - HBase
    - Amazon S3

2. Create RDD from collection

Simple example of creating an RDD from a list in Scala and Python

```sh
# Python example
data = [1,2,3,4,5]
distData = sc.parallelize(data)
```

3. Apply a transformation on existing RDD to create a new RDD

## What is Parallel Programming

- is a simaltaneous use of multiple compute resources to solve a computational problem
- breaks problem into disrete parts that can be solved concurrently
- runs simaltaneous instructions on multiple processors
- employs an overall control/coordination mechanism

## RDD and Parallel Programming

- You can create an RDD by parallelizing an array of objects, or by splitting a dataset into partitions
- Spark runs one task for each partition of the cluster

## Resilience and Spark

- Resilent Distributed Datasets
    - are always recoverable as they are immutable
    - can persist or cache datasets in memory across operations, which speeds iterative operations