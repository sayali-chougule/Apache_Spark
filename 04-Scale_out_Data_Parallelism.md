# Scale out / Data Parallelism in Apache Spark

## Apache Spark Components

#### 1. Data Storage
- Datasets load from data storage into memory
- Any Hadoop compatible data source is acceptable

#### 2. Compute Interface 
- Spark has API interface in Python, Scala, Java

#### 3. Cluster Management Framework

- Handles distributed computing aspect of Spark
- Standalone, Mesos, YARN, and Kubernetes
- Essential for scaling big data

## Spark Core

- Is a base engine
- Is fault tolerant
- Performs large scale parallel and distributed data processing
- Manages memory
- Schedules tasks
- Houses APIs that define RDDs
- Contains a distributed collection of elements that are parallelized across the cluster