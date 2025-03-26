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

1. Clone the repository:
```bash
git clone https://github.com/yourusername/data-engineering-pipeline.git
cd data-engineering-pipeline
