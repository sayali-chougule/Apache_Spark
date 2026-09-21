# RDDs in Parallel Programming and Spark

## Resilient Distributed Datasets

- Spark's primary data abstraction 
- Partitioned across nodes of cluster

## RDD Transformations

Transformations
- create new RDD from existing one
- are "lazy" because the results are only computed when evaluated by actions

- The "map" transformation passes each element of dataset through a function and returns a new RDD

**Example**
```sh
map()
transformation
```

## RDD Actions

- Actions return a value to driver program after running a computation

**Example**
```sh
reduce()
An action that aggregates all RDD elements
```

## Directed Acyclic Graph (DAG)

- A graphical data structure with edges and vertices
- Every new edge is obtained from an old vertex
- In Apache Spark DAG, vertices represents RDDs and edges represent operarions such as transformations or actions
- If a node goes down, Spark replicates the DAG and restores the node

## Transformations and Actions

- Spark creates the DAG when creating an RDD
- Spark enables the DAG schedular to perform a transformation and updates the DAG
- The DAG now points to the new RDD
- The pointer that transforms RDD is returned to the Spark driver program
- If there is an action, the driver program that calls the action evaluates the DAG only after Spark completes the action