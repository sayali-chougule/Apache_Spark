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