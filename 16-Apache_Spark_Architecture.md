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