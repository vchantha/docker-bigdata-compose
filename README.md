# Big Data Ecosystem with Docker Compose

## Introduction

This project provides a comprehensive guide to setting up a big data ecosystem using Docker Compose. The stack includes various components for data ingestion, processing, storage, and querying, making it suitable for big data workflows.

---

## Architecture

The architecture of the big data platform is illustrated below:

![Architecture](images/dataplatform.png)

---

## Prerequisites

Before starting, ensure the following:

- Docker and Docker Compose are installed.
- Sufficient resources (CPU, RAM, and Disk) are allocated for Docker.
- Required ports for services are available.
- Clone this repository and navigate to the `docker-bigdata-compose` directory:

```bash
git clone https://github.com/amhhaggag/bigdata-ecosystem-sandbox.git
cd docker-bigdata-compose
```

---

## Components Overview

### 1. Nifi (Data Ingestion)

- Define and configure data ingestion flows.
- Expose Nifi UI on `http://localhost:8080`.

### 2. Spark (Compute)

- Set up Spark master and worker nodes.
- Verify Spark UI on `http://localhost:8081`.

### 3. Kafka + Flink (Streaming)

- Deploy Kafka brokers and Zookeeper.
- Create Kafka topics and set up Flink for stream processing.

### 4. Trino + Hive (RDBMS)

- Deploy Hive Metastore and configure it with a database.
- Set up Trino for querying data.

### 5. Hadoop / Minio (Datastore)

- Deploy Hadoop HDFS or Minio for storage.
- Configure storage paths and permissions.

---

## Deployment Guide

### Step 1: Start All Services

Run the following commands to start each service:

```bash
docker compose up -d minio
docker compose up -d namenode datanode nodemanager resourcemanager historyserver
docker compose up -d hive-metastore hive-server
docker compose up -d spark-master spark-worker
docker compose up -d trino
docker compose up -d nessie
docker compose up -d airflow-db airflow
docker compose up -d jobmanager taskmanager
docker compose up -d kafka schema-registry postgresql conduktor-console conduktor-monitoring
docker compose up -d nifi-zookeeper nifi
```

---

## Verification

Verify that the services are running:

- **Nifi**: `http://localhost:8080`
- **Spark UI**: `http://localhost:8081`
- **Kafka**: Use Kafka CLI tools or a UI like Kafdrop.
- **Flink**: `http://localhost:8082`
- **Trino**: `http://localhost:8083`
- **Hadoop/Minio**: `http://localhost:9000` (Minio) or HDFS CLI.

---

## Testing the Ecosystem

- Ingest data using Nifi.
- Process data with Spark.
- Stream data using Kafka and Flink.
- Query data with Trino and Hive.
- Store and retrieve data using Hadoop/Minio.

---

## Notes

- Modify the `docker-compose.yaml` file to customize configurations.
- Ensure proper networking between services.
- Monitor logs for troubleshooting: `docker-compose logs -f`.

---

## Credits

This setup is inspired by the repository: [bigdata-ecosystem-sandbox](https://github.com/amhhaggag/bigdata-ecosystem-sandbox.git)

---

Happy Big Data Engineering!