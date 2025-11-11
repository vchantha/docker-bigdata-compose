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
    git clone git@github.com:vchantha/docker-bigdata-compose.git
    cd docker-bigdata-compose
    ```

---

## Components Overview


### 1. PostgreSQL

- Deploy a PostgreSQL database for metadata storage.

- Ports: `5432:5432`


### 2. MinIO (Object Storage)

- Deploy MinIO for object storage.

- Ports: `9000:9000` (server), `9001:9001` (console)


### 3. Hadoop (HDFS)

- Deploy NameNode, DataNode, NodeManager, ResourceManager, and HistoryServer.

- Ports: `9870` (NameNode), `8042` (NodeManager), `8088` (ResourceManager)


### 4. Hive

- Deploy Hive Metastore and Hive Server.

- Ports: `9083` (Metastore), `10000` (Hive Server)


### 5. Spark

- Deploy Spark Master and Worker nodes.

- Ports: `7077` (Master), `8080` (Master UI), `8081` (Worker UI)


### 6. Airflow

- Deploy Airflow for workflow orchestration.

- Ports: `8090` (Airflow UI)


### 7. Trino

- Deploy Trino for querying data.

- Ports: `8080`


### 8. Kafka

- Deploy Kafka for messaging and streaming.

- Ports: `9092`

---

## Deployment Guide

### Step 1: Start All Services

Follow these steps to deploy the services:

1. **PostgreSQL**:

    ```bash
    docker compose up -d postgres
    ```

2. **MinIO**:

    ```bash
    docker compose up -d minio
    ```

3. **Hadoop (HDFS)**:

    ```bash
    docker compose up -d namenode datanode nodemanager resourcemanager historyserver
    ```

4. **Hive**:

    ```bash
    docker compose up -d hive-metastore hive-server
    ```

5. **Spark**:

    ```bash
    docker compose up -d spark-master spark-worker
    ```

6. **Airflow**:

    ```bash
    docker compose up -d airflow-db airflow
    ```

7. **Trino**:

    ```bash
    docker compose up -d trino
    ```

8. **Kafka**:

    ```bash
    docker compose up -d kafka
    ```

---

## Verification

Verify that the services are running:

- **PostgreSQL**: `5432`
- **MinIO**: `http://localhost:9000` (server), `http://localhost:9001` (console).
- **Hadoop**: `http://localhost:9870` (NameNode), `http://localhost:8042` (NodeManager), `http://localhost:8088` (ResourceManager).
- **Hive**: `http://localhost:9083` (Metastore), `http://localhost:10000` (Hive Server).
- **Spark**: `http://localhost:8080` (Master UI), `http://localhost:8081` (Worker UI).
- **Airflow**: `http://localhost:8090`.
- **Trino**: `http://localhost:8080`.
- **Kafka**: `http://localhost:9092`.

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

This is Dashboard for reference:
https://www.slideteam.net/blog/top-10-banking-dashboard-templates-with-samples-and-examples
https://github.com/Udbhav1405/Banking-Dashboard

```bash
---

Happy Big Data Engineering!