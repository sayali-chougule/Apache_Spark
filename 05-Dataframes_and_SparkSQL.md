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