Kafka Data Pipeline
Overview

This Kafka data pipeline consists of a Kafka cluster with multiple topics, two producers that generate
data, and three consumers that consume and process the data. The data is generated based on a
realistic financial transactions use case using a Kafka client library. The consumers perform different
processes on the data, such as aggregating company events by company ID, calculating real-time
statistics on stock inventory, and filtering out fraudulent financial transactions. The pipeline is also
integrated with an external system, such as a MongoDB or SQL database.
Data Description

Brief description of some of the most common data available on Yahoo Finance:
• Stock Price Data: Historical and real-time data on stock prices for publicly traded companies,
including the opening price, closing price, high price, low price, and trading volume.
• Financial Statements: Quarterly and annual financial statements for publicly traded companies,
including the balance sheet, income statement, and cash flow statement.
• Market Data: Information on market capitalization, trading volume, and other key market
metrics for individual stocks and broader market indices.
• News and Analysis: Articles and analysis on breaking news and trends in the financial markets,
including company news, analyst reports, and economic indicators.
• Charting and Technical Analysis: Charting tools and technical analysis indicators to help
investors and traders analyze market trends and make informed decisions.
• Options and Derivatives Data: Data on options and other derivative securities, including strike
price, expiration date, and open interest.
The data is generated based on a realistic financial transactions use case and sent to different Kafka
topics.
Pipeline Setup
To set up and run the pipeline, follow these steps:
1. Install Apache Kafka and ZooKeeper.
2. Start ZooKeeper by running the following command in a terminal:
Code :
bin/zookeeper-server-start.sh config/zookeeper.properties
3. Start Kafka brokers by running the following command in a new terminal:
Code:
kafka-server-start.sh config/server1.properties
kafka-server-start.sh config/server2.properties
kafka-server-start.sh config/server3.properties
4. Create Kafka topics with different replication factors, retention periods, and partition counts.
For example:
Code:
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 --
partitions 4-- topic topic1
5. Create kafka producers
Code:
kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic1,topic2
kafka-console-producer.sh --bootstrap-server localhost:9092 --topic topic3
6. Create kafka consumers
Code:
kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --t opic
topic1
kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 -- topic
topic2
kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 -- topic
topic3
