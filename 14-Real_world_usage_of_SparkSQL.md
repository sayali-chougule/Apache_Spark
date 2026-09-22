# Real-world usage of SparkSQL

## Creating a view in Spark SQL

- Creating a table view in Spark SQL is required to run SQL queries programatically on a DataFrame

- View is temporary table to run SQL queries
    - A temporary view provides a local scope within the current Spark session
    - A global temporary view provides global scope within the Spark application

## Creating a view in Spark

```sh
# Create a DataFrame from a file
df = spark.read.json("people.json")
# Create a temp view
df.createTempView("people")
# Run SQL queries
spark.sql("SELECT * FROM people").show()
```