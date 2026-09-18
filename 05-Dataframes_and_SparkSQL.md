# Dataframes and SparkSQL

## SparkSQL

- Is a Spark module for a structured data processing
- Used to query structured data inside Spark programs, using either SQL or a familiar DataFrame API
- Usable in Java, python, R and Scala
- Runs SQL queries over imported data and existing RDDs independently of API or programming language.

## Spark SQL Example

- Spark SQL query using Python

```sh
results = spark.sql(
    "SELECT * FROM people")
names = results.map(lambda p:
p.name)
```

## Spark SQL - Benefits

- Includes a cost based optimizer, columnar storage, and code generation to make queries fast
- scales to thoudands of nodes and multi-hour queries using the Spark engine, which provides full mid-query fault tolerance
- Provides a programming abstraction called DataFrames and can also act as distributed SQL query engine


## DataFrames

- Distributed collection of data organized into named columns
- Conceptually equivalent to a table in a relational database or a dataframe in R/Python, but with reacher optimizations
- Built on top of RDD API
- Uses RDDs
- Performs relational queries