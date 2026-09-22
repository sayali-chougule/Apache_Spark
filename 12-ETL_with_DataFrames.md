# ETL with DataFrames

## Basic DataFrame Operations
- **Read** the data
- **Analyse** the data
- **Transform** the data
- **Load** data into a database
- **Write** data back to the disk

### 1. Read the Data
- Create a DataFrame
- Create a DataFrame from an existing DataFrame

*Code Sample*

```sh
import pandas as pd
df = pd.read_csv('file_name.cvs')
df1 = spark.createDataFrame(df)
```

### 2. Analyze the data 

1. Using printSchema

```sh
df1.printSchema()
```

2. Using select function

```sh
df1.select('col1').show(5)
```
### 3. Transform the data

*Guidelines*

- Keep only the relevant data
- Apply filters, joins, sources and tables, column operations, grouping and aggregations and other functions
- Apply domain-specific data augmentations process

1. using filter

```sh
df1.filter(df1['age'] < 18).show(5)
```

2. using aggregation

```sh
car_counts = df1.groupby(['cyl']).agg({"wt":"count"})\ .sort("count(wt)", ascending = False).show(5)
```

#### Loading or Exporting the Data

Is the final step of ETL pipeline
- Export to another database
- Export to disk as JSON files
- Save the data to the Postgres database
- Use an API to export data