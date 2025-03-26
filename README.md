# KafkaSpark: Containerized User Data Processing Engine

![Apache Airflow](https://img.shields.io/badge/Apache_Airflow-2.5.1-blue)
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-3.3.1-red)
![Apache Spark](https://img.shields.io/badge/Apache_Spark-3.4.1-orange)
![Cassandra](https://img.shields.io/badge/Cassandra-Latest-green)
![Docker](https://img.shields.io/badge/Docker-Compose-lightblue)
![Python](https://img.shields.io/badge/Python-3.11-yellow)

A complete data engineering pipeline that demonstrates streaming data from an API through multiple distributed systems using containerized architecture.

## System Architecture

![Architecture Diagram](images/architecture.png)

The system consists of the following components:

- **Data Source**: Random User Generator API
- **Workflow Orchestration**: Apache Airflow (with PostgreSQL backend)
- **Message Queue**: Apache Kafka and Zookeeper
- **Stream Processing**: Apache Spark (Master-Worker)
- **Database**: Apache Cassandra
- **Monitoring**: Kafka Control Center and Schema Registry

## Features

- Scheduled API data fetching with Apache Airflow
- Real-time data streaming with Kafka
- Distributed processing with Spark
- Scalable NoSQL storage with Cassandra
- Complete containerization with Docker Compose
- Fault-tolerance and error recovery
- Monitoring and observability

## Getting Started

### Prerequisites

- Docker and Docker Compose
- At least 8GB RAM for running all containers
- Git

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/faseehahmed26/kafkaspark-processing-engine.git
cd data-engineering-pipeline
# 2. Start the Docker containers:
docker-compose up -d
```
Access the various interfaces:

Airflow: http://localhost:8080 (admin/admin)
Kafka Control Center: http://localhost:9021
Spark Master UI: http://localhost:8080



Project Structure
```bash
├── dags/                  # Airflow DAG definitions
│   └── kafka_stream.py    # API to Kafka DAG
├── scripts/               # Utility scripts
│   └── entry_point.sh     # Containers startup script
├── spark/                 # Spark jobs
│   └── spark_stream.py    # Kafka to Cassandra streaming job
├── docker-compose.yml     # Container configuration
└── README.md              # Documentation
```
Usage
Running the Pipeline

Enable the Airflow DAG "user_automation" from the Airflow UI
Trigger the DAG to start fetching data from the API
Check the Kafka Control Center to monitor incoming messages
Verify data is being processed by examining Spark Master UI
Query Cassandra to confirm data storage:

```bash
Connect to Cassandra
docker exec -it cassandra cqlsh -u cassandra -p cassandra
# View stored data
SELECT * FROM sparkstreams.created_users LIMIT 10;
```

Scaling the System
Adding Spark Workers
To add more Spark workers, modify the docker-compose.yml file:
```yaml
spark-worker-2:
  image: bitnami/spark:latest
  container_name: spark-worker-2
  hostname: spark-worker-2
  depends_on:
    - spark-master
  environment:
    - SPARK_MODE=worker
    - SPARK_MASTER_URL=spark://spark-master:7077
    - SPARK_WORKER_MEMORY=1G
    - SPARK_WORKER_CORES=1
  networks:
    - app-network
```
Kafka Scaling
For production environments, add more Kafka brokers and adjust Zookeeper accordingly.
License
This project is licensed under the MIT License - see the LICENSE file for details.
## Acknowledgements

- [Apache Airflow](https://airflow.apache.org/)
- [Apache Kafka](https://kafka.apache.org/)
- [Apache Spark](https://spark.apache.org/)
- [Apache Cassandra](https://cassandra.apache.org/)
- [Random User Generator API](https://randomuser.me/)
