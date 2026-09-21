# Data-frames and Datasets in Spark

## Datasets

A dataset is distributed collection of data that
- consists of strongly typed JVM objects
- provides combine benefits for both RDDs and Spark SQL

## Datasets Features

- Are immutable, meaning that data cannot be deleted or lost
- Feature an encoder that converts JVM objects to a tabular representation
- Extend DataFrame type-safe and object oriented API capabilities
- Work with both Scala and Java APIs

## Datasets in Spark - Benefits

- Provide compile-time type safety
- Compute faster than RDDs
- Offer the benfits of Spark SQL and Dataframes
- Optimize query using Catalyst and Tungsten
- Enable improved memory usage and caching
- Use dataset API functions for aggregate operations including sum, avg, join and group by