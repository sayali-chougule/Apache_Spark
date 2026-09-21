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

## Transformation Examples
```
+----------------+------------------------------------------------------------+
| Transformation | Discription                                                |
+----------------+------------------------------------------------------------+
|map (*func*)    |Returns a new distributed dataset formed by passing each    |       
|                |element of source through a function *func*                 |
+----------------+------------------------------------------------------------+
|Filter (*func*) |Returns a new dataset formed by selecting those             |
+----------------+------------------------------------------------------------+
|Distinct        |Returns a new dataset that contains the distinct elements of|
|([numTasks])    |the source dataset                                          |
+----------------+------------------------------------------------------------+
|flatmap (*func*)|Similar to map (*func*)                                     |
|                |Can map to each input item to zero or more output items     |
|                |*Func* should return a Seq rather than a single item        |
+----------------+------------------------------------------------------------+
```

## Action Examples
```
+-------------------------+--------------------------------------------------+
|Action                   |Description                                       |
+-------------------------+--------------------------------------------------+
|reduce (*func*)          |*func* takes two arguements and returns one       |   
|aggregates dataset       |Is cummutative                                    |
|elements using function  |Is associative                                    |
|(*func*)                 |Can be correctly computed in parallel             |
+-------------------------+--------------------------------------------------+
|take (n)                 |Retuns an array with first n element              |
+-------------------------+--------------------------------------------------+
|collect()                |Returns all elements as array                     |
+-------------------------+--------------------------------------------------+
|takeOrdered              |Returns *n* elements ordered in ascending order   |
|(n, key=*func*)          |or as specified by the optional key function      |
+-------------------------+--------------------------------------------------+
```