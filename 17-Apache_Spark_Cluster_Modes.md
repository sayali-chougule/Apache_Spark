# Apache Spark Cluster Modes

## Spark Cluster Manager

- Communicates with a particular cluster to acquire resources for the running application
- Runs as a service outside the application and abstracts the cluster type

## Types of Cluster Managers

- **Spark Standalone:** comes with Spark, best for setting simple cluster
- **Apache Hadoop YARN:** (Yet Another Resource Negotiator) Cluster manager from the Hadoop project
- **Apache Mesos:** General-purpose cluster manager with additional benefits
- **Kubernates:** Open-source system for running containerized applications

## Spark Standalone Benefits

- Built into the Spark installation, so no additional dpendencies to deploy 
- Fastest way to setup a Spark cluster and get running
- Specifically designed for Spark, not general purpose

## Spark Standalone components

- **Worker** - run an executive process to receive tasks
- **Master** - connects and adds workers to the cluster

## Set up Spark Standalone

1. Start the master to output the master URL

```sh
./sbin/start-master.sh
```

2. Start worker(s) with the Master URL

```sh
./sbin/start-slave.sh spark://<master-spark-url>:7077
```

3. Launch Spark application on cluster by specifying the Master URL

```sh
./bin/spark-submit \
--master spark://<spark-master-url>:7077 \
<additional configuration>
```

## Apache Hadoop YARN

- When choosing Apache Hadoop YARN, consider that it:
    - is general purpose
    - supports many other big data ecosystem frameworks
    - requires its own configuration and setup
    - has dependencies, making it more complex to deploy than Spark Standalone

## How to run Spark on existing YARN cluster

- 1. Specify the Master option '--master YARN' with 'spark-submit'

```sh
./bin/spark-submit \
--master YARN \
<additional configuration>
```

- 2. Spark will automatically connect with YARN using Hadoop configuration

## Apache Mesos

- **Apache Mesos** Cluster Managers can run Spark with other benefits, such as making partitioning:
    - **Scalable** between many Spark instances
    - **Dynamic** between Spark and other data frameworks

## Kubernetes

- Kubernetes cluster managers can run containerized applications, making it easier to:
    - Automate deployment
    - Simplify dependency management
    - Scale the cluster

- To launch Spark Application on Kubernetes

```sh
./bin/spark-submit \
--master k8s://https://<k8s-apiserver-host>:<k8s-apiserver-port> \
<additional configuration>
```

## Local Mode

- Spark can also run in local mode which:
    - Does not connect to cluster, making it easy to get started
    - Runs in same process that calls 'spark-submit' and uses threads for running executor tasks
    - can be useful for testing or debugging a Spark application 
    - Runs a Spark application locally within a single process which can limit performance

- To run Spark in local mode, use master option '--master local[#]' where # specifies number of cores to use

```sh
# Launch Spark in local mode with 8 cores
./bin/spark-submit \
--master local[8] \
<additional configuration>
```

- Use an asterisk '*' to specify using all available cores

```sh
# Launch Spark in local mode with all available cores
./bin/spark-submit \
--master local[*] \
<additional configuration>
```