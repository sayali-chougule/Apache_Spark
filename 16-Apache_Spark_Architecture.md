# Apache Spark Architecture

## Spark Application Processes

- A Spark application has two main process
    1. **Driver Program**: A single process that creates work for cluster
    2. **Executers**: Multiple processors throughout the cluster that do the work in parallel

## Spark Context

- Communicates with Cluster Manager
- Is defined in the Driver, with one Spark Context per Spark Application 

## Spark Jobs 

- Jobs are communications that can be executed in parallel
- The Spark context devides Jobs into Tasks to be executed on Cluster

## Spark Tasks

- Tasks from a given job operate on different data subsets called Partitions and can be executed in parallel

## Spark Executors

- A **Worker** is a cluster node that can launch executor processes to run tasks
- Each **Executor** is allocated a set number of cores that each run one task at a time
- Increasing Executors and cores increases **cluster parallelism**
- Ideally, limit Executor x core combinations to total cores per node

## Spark Stages and Shuffles

- A Stage is a set of tasks within a job that can be completed on current local data partition
- A **Shuffle** marks the boundary between Stages
- Stages connect to form dependency graph

## Why shuffle data

- A shuffle is 
    - **Costly** - requiring data serialization, disk and network I/O
    - Necessary when an operation requires data outside the current partition of task   
    - How Spark re-disctributes the dataset across the cluster


## Driver Deploy Modes

There are two deploy modes:
    - **Client Mode** : the application submitter launches the driver process *outside* the cluster
    - **Cluster Mode** : the framework launches the driver process *inside* the cluster