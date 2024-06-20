# Kafka Data Pipeline

This project implements a complex data pipeline using Apache Kafka. The pipeline consists of a Kafka cluster with multiple topics, producers that generate data, and consumers that process the data. The pipeline integrates with an external system (MongoDB or SQL database).

## Table of Contents
- [Overview](#overview)
- [Data Description](#data-description)
- [Pipeline Setup](#pipeline-setup)
  - [Kafka Installation](#kafka-installation)
  - [Kafka Cluster Setup](#kafka-cluster-setup)
  - [Creating Kafka Topics](#creating-kafka-topics)
  - [Writing Producers](#writing-producers)
  - [Writing Consumers](#writing-consumers)
  - [Integrating with External Systems](#integrating-with-external-systems)
  - [Testing the Pipeline](#testing-the-pipeline)
- [Screenshots](#screenshots)
- [License](#license)

## Overview

This Kafka data pipeline consists of a Kafka cluster with multiple topics, two producers that generate data, and three consumers that consume and process the data. The data is generated based on a realistic financial transactions use case using a Kafka client library. The consumers perform different processes on the data, such as aggregating company events by company ID, calculating real-time statistics on stock inventory, and filtering out fraudulent financial transactions. The pipeline is also integrated with an external system, such as a MongoDB or SQL database.

## Data Description

The data is generated based on a realistic financial transactions use case and sent to different Kafka topics. Common data types include:
- **Stock Price Data:** Historical and real-time stock prices, including opening, closing, high, low prices, and trading volume.
- **Financial Statements:** Quarterly and annual financial statements, including balance sheets, income statements, and cash flow statements.
- **Market Data:** Market capitalization, trading volume, and other key market metrics.
- **News and Analysis:** Articles and analysis on financial markets, company news, analyst reports, and economic indicators.
- **Charting and Technical Analysis:** Charting tools and technical analysis indicators for market trend analysis.
- **Options and Derivatives Data:** Data on options and other derivative securities, including strike price, expiration date, and open interest.

## Pipeline Setup

### Kafka Installation

1. **Download Apache Kafka:**

    ```bash
    wget https://downloads.apache.org/kafka/2.8.0/kafka_2.13-2.8.0.tgz
    ```

2. **Extract the tar file:**

    ```bash
    tar -xzf kafka_2.13-2.8.0.tgz
    cd kafka_2.13-2.8.0
    ```

### Kafka Cluster Setup

1. **Start ZooKeeper:**

    ```bash
    bin/zookeeper-server-start.sh config/zookeeper.properties
    ```

2. **Start Kafka brokers:**

    ```bash
    bin/kafka-server-start.sh config/server1.properties
    bin/kafka-server-start.sh config/server2.properties
    bin/kafka-server-start.sh config/server3.properties
    ```

### Creating Kafka Topics

Create Kafka topics with different replication factors, retention periods, and partition counts. Example:

```bash
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 --partitions 4 --topic topic1
```

### Writing Producers

1.**Create Kafka producers:** 
   
  ```bash
      kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic1
      kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic2
      kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic3
  ```

### Screenshots

#### Producer:
![image](https://github.com/MuhammadHaziq1337/Kafka-Data-Pipeline/assets/148570176/e2f4e395-05d6-436c-bbe5-9f61c03fc15e)


#### Consumer 1:
![image](https://github.com/MuhammadHaziq1337/Kafka-Data-Pipeline/assets/148570176/4188c5dc-668d-464c-8147-2d3f44261ee9)


#### Consumer 2:
![image](https://github.com/MuhammadHaziq1337/Kafka-Data-Pipeline/assets/148570176/a2c4eb7d-9b68-46bd-bfb3-78ad1211b6e9)


#### Consumer 3:
![image](https://github.com/MuhammadHaziq1337/Kafka-Data-Pipeline/assets/148570176/ab498e92-95a7-4c19-a9df-b4322a8b35d3)


#### Database:
![image](https://github.com/MuhammadHaziq1337/Kafka-Data-Pipeline/assets/148570176/3262f407-f909-444c-93d0-1d1ba189366f)
