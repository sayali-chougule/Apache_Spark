# Transformations and Optimization Techniques

## Narrow transformations 
- Spark works within partitions without shuffling data between them. 
- They're applied locally to each partition, avoiding data exchange. 

### Examples of narrow transformations

1. **Map**: Applying a function to each element in the data set

```sh
from pyspark import SparkContext
sc = SparkContext("local", "MapExample")
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)
mapped_rdd = rdd.map(lambda x: x * 2)
mapped_rdd.collect() 
# Output: [2, 4, 6, 8, 10]
```
2. **Filter**: Selecting elements based on a specified condition

```sh
from pyspark import SparkContext
sc = SparkContext("local", "FilterExample")
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)
filtered_rdd = rdd.filter(lambda x: x % 2 == 0)
filtered_rdd.collect() # Output: [2, 4]
```

3. **Union**: Combining two data sets with the same schema

```sh
from pyspark import SparkContext
sc = SparkContext("local", "UnionExample")
rdd1 = sc.parallelize([1, 2, 3])
rdd2 = sc.parallelize([4, 5, 6])
union_rdd = rdd1.union(rdd2)
union_rdd.collect() # Output: [1, 2, 3, 4, 5, 6]
```

## Wide transformations 
- Spark involves redistributing and shuffling data between partitions, often leading to more resource-intensive and complex operations

### Examples of wide transformations

1. **GroupBy**: Aggregating data based on a specific key

```sh
from pyspark import SparkContext
sc = SparkContext("local", "GroupByExample")
data = [("apple", 2), ("banana", 3), ("apple", 5), ("banana", 1)]
rdd = sc.parallelize(data)
grouped_rdd = rdd.groupBy(lambda x: x[0])
sum_rdd = grouped_rdd.mapValues(lambda values: sum([v[1] for v in values]))
sum_rdd.collect() 
# Output: [('apple', 7), ('banana', 4)]
```