# Spark Configuration

## Spark Configuration Types

```
+----------------------------+--------------------------------------------------------+
| Configuration Type         | Parameters                                             |
+----------------------------+--------------------------------------------------------+
| Properties                 | Adjust and control application behavior                |
+----------------------------+--------------------------------------------------------+
| Environmental Variables    | Adjust settings on a per-machine basis                 |
+----------------------------+--------------------------------------------------------+
| Logging                    | Control how logging is output using                    |
|                            | `conf/log4j-defaults.properties`                       |
+----------------------------+--------------------------------------------------------+
```

## Spark Configuration Location 

- Configuration files are located under the `conf/` directory in the Spark installation
- Files are not created by default, however Spark provides template files that can be renamed as shown in table

```
+-------------------------+-------------------------------------+---------------------------+
| Configuration Type      | Template file                       | Actual file               |
+-------------------------+-------------------------------------+---------------------------+
| Spark properties        | spark-defaults.conf.template        | spark-defaults.conf       |
+-------------------------+-------------------------------------+---------------------------+
| Environment variables   | spark-env.sh.template               | spark-env.sh              |
+-------------------------+-------------------------------------+---------------------------+
| Logging properties      | log4j.properties.template           | log4j.properties          |
+-------------------------+-------------------------------------+---------------------------+
```

## Spark Property Configuration

- We can set properties:
    1. Programmatically when creating SparkSession or using a SparkConf object
    
    ```sh 
    # Set a master and additional conf when creating a session

    spark = SparkSession\
            .builder\
            .master("spark://<master-url>:7077")\
            .config("<key>", "<value>")\
            .getOrCreate()
    ```

    2. In the file `conf/spark-defaults.conf`

    3. When launching `Spark-submit` with arguments `--master`, or `--conf<key>=<value>`