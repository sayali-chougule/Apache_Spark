# Run an Apache Spark Application

## spark-submit

- spark-submit script:
    - Spark's Unified Interface for submitting applications
    - Found in the 'bin/' directory
    - Easily switches from local to cluster mode by changing a single argument
    - Works the same way regardless of cluster manager type or application language

    ```sh
    ./bin/spark-submit <config and options> <application files>
    ```
- spark-submit script will:
    1. Parse command line arguements/options
    2. Read additional configuration specified in `conf/spark-defaults.cof`
    3. Connect to the cluster manager specified with the `--master` argument or run in local
    4. Transfer application (JARs or Python files) and any additional files specified to be distributed and run in the cluster

## Common 'spark-submit' Options

```
+-------------------------------------------+---------------------------+--------------+
| Option/Setting                            | Form                      | Mandatory    |
+-------------------------------------------+---------------------------+--------------+
| Tell Spark what cluster manager to        | '--master'                | Yes          |
| connect with                              |                           |              |
+-------------------------------------------+---------------------------+--------------+
| Specify the program entry point if using  | '--class <full-class-name>| Yes          |
| Java or Scala application                 |                           |              |
+-------------------------------------------+---------------------------+--------------+
| Set how the driver is deployed (Client or | 'deploy-mode              | No           |
| cluster). Default is client mode          |                           |              |
+-------------------------------------------+---------------------------+--------------+
| Set CPU core and memory usage in          | '--executor-cores' and    | No           |
| executors                                 | '--executor-memory'       |              |
+-------------------------------------------+---------------------------+--------------+
| See available options by cluster manager  | ' ./bin/spark-submit-help'| N/A          |
+-------------------------------------------+---------------------------+--------------+
```

## 'spark-submit' Application Files

Final arguments depend on application language

#### Java or Scala

```sh
<application-jar-path> <application-args> 
```
- Specifies the location of the JAR with your application and dependencies, followed by any arguments specific to the application

#### Python 


```sh
<application-py-path> <application-args>
```

- Specifies the application python script followed by arguments specific to the application. Add files with `.py`, `.egg` or `.zip` using `--py-files` arguments

## spark-submit Examples

1. Launch Scala SparkPi using a jar, with master YARN. Estimate Pi with 1000 samples

```sh
# Launching Scala SparkPi to a YARN cluster

./bin/spark-submit \
--class org.apache.spark.examples.SparkPi \
--master YARN \
/path/to/examples.jar \
1000
```

2. Launch Python SparkPi to a Spark standalone cluster with master at 207.184.161.138   

```sh
./bin/spark-submit \
--master spark://207.184.161.138:7077 \
examples/src/main/python/pi.py 1000
1000
```

## Application Dependencies

- To manage Spark dependencies:
    - Bundle project or libraries with application so they are accessible to driver and executive processes 
    - For Java or Scala based programs, create an uber-jar with application and dependencies together so it is easy to distribute to the cluster

## Python Application Dependencies

- To manage Python application dependencies, esure:
    - cluster nodes can access the required dependencies with same version
    - same python version is used
    - use the `--py-files` argument so that `.py`, `.zip` or `.egg` files can be distributed to the cluster

    ```sh
    # Launching a PySpark application with dependency on "my_python_package"

    ./bin/spark-submit <config and options> \
    --py-files my_python_package.zip \
    my_pyspark_application.py
    ```

## Spark Shell

- Simple way to learn Spark API
- Powerful tool to analyze data interactively
- Use in local mode or with a cluster, same options as `spark-submit`
- Can initiate in Scala (`bin/spark-shell`) and Python (`bin/pyspark`)

## Spark Shell Environment

- For both Scala and Python shells:
    - SparkContext is automatically initialized and is available as `sc`
    - SparkContext is automatically available as `spark`
    - Expressions are entered into the shell and then evaluated in the driver to become jobs that are scheduled as tasks for the cluster