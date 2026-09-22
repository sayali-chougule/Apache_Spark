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

```sh
# Create a global temp view
df.createGlobalTempView("people")
# Run SQL query
spark.sql("SELECT * FROM global_temp.people").show()
```

## Aggregating Data

- Used to aggregate data over columns
    - DataFrames contain inbuild common aggregation functions - count(), countDistinct(), avg(), max(), and others
    - Alternatively, aggregate using SQL queries and tableviews

## Example

```sh
import pandas as pd
mtcars = pd.read_csv('mtcars.csv')
sdf = spark.createDataFrame(mtcars)
sdf.select('mpg').show(5)
```

```sh
# Using a SQL Query and Table view
sdf.createTempView("cars")
sql("SELECT cyl, COUNT(*) FROM cars GROUP BY cyl ORDER BY 2 DESC")
```

## Spark SQL Data Sources

1. Parquet Files
- Supports reading/writing and preserving data schema
- Spark SQL can also run queries without loading a file

2. JSON Datasets
- Spark infers the schema and loads the dataset as a DataFrame

3. Hive Tables
- Spark supports reading and writing data stored in Apache Hive