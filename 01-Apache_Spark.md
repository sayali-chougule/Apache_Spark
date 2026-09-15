# Apache Spark

## Apache Spark Attributes

Spark is an **open** source **in-memory application** framework for **distributed** data processing and **iterative** analysis on **massive** data volumes

- *Spark* is entirely open source
- *In-memory* means that all the operations happen within the memory or RAM
- *Distributed* data uses Spark
- Spark is ideal for *massive* datasets

- Spark is written in predominantly in Scala and runs of JVMs

## Distributed Computing

- A group, or a cluster, of computers working together to appear as one system to the end 
user
- The term distributed computing often used interchangeably with the parallel computing as both are similar

## Parallel Vs Distributed Computing

- Parallel computing processors access shared memory

- Distributed Computing processors usually have their own private or distributed memory

## Distributed Computing benefits

1. **Scalability and modular growth**
- Distributed systems are inherently scalable as they work across multiple machines and scale horizontally

- A user can add additional machines to handle the increasing workload instead of repeatedly updating a single system, with virtually no cap for scalability

2. **Fualt Tolerance and redundancy**
- Distributed computing provides redundancy that enables the business continuity

## Spark Benefits

- Supports a computing framework for large scale data processing and analysis

- Provides a parallel and distributed processing, scalability and fault tolerance on commodity hardware

- Provides speed due to in memory processing

- Creates a comprehensive, unified framework to manage big data processing

- Enables programming flexibility with easy-to-use Python, Scala, and Java APIs

## Apache Spark and MapReduce Compared

### Traditional Approach:

- Create MapReduce jobs for complex jobs, interactive query, and online event hub processing involves lots of (slow) disk I/O
i.e traditional MapReduce jobs create iterations that requires reads and writes to disk or HDFS. These reads and writes are time-consuming and expensive

#### Solution:
Apache Spark solves the read/write problem encountered with MapReduce by keeping much of the data required in memory and avoiding expensive disk I/O, thus reducing overall time by orders of magnitude

## Spark and Big Data

### Data Engineering

- Core spark engine
- clusters and executors
- Cluster management 
- SparkSQL
- Catalyst Tungstem Dataframes

### DS and ML

- SparkML
- DataFrames
- Streaming



 
