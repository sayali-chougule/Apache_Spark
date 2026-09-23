# Transformations and Optimization Techniques

## Narrow transformations 
- Spark works within partitions without shuffling data between them. 
- They're applied locally to each partition, avoiding data exchange. 

### Examples of narrow transformations

**Map: Applying a function to each element in the data set**


```sh
from pyspark import SparkContext
sc = SparkContext("local", "MapExample")
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)
mapped_rdd = rdd.map(lambda x: x * 2)
mapped_rdd.collect() 
# Output: [2, 4, 6, 8, 10]
```

Filter: Selecting elements based on a specified condition.

## Wide transformations 
- Spark involves redistributing and shuffling data between partitions, often leading to more resource-intensive and complex operations

