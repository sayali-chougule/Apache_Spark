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