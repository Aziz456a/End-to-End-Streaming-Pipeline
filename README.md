# End-to-End-Streaming-Pipeline

This repository contains an end-to-end streaming data pipeline that leverages:

Apache Kafka for message ingestion and queuing
Apache Spark for streaming data processing
Python (producers/consumers and utility scripts) used in Pycharm as an IDE
Avro for data serialization and backup
InfluxDB for time-series data storage
Amazon DynamoDB for Cloud High Availibility NoSQL data storage

Table of Contents:

Overview
Architecture
Features
Prerequisites
Installation & Setup
1. Clone the Repository
2. Install Dependencies
3. Set Up Kafka
4. Set Up Spark
5. Set Up InfluxDB
6. Set Up DynamoDB
7. Configure Environment Variables
Usage
Producer
Consumer
Avro Backup
Influx Testing
Spark Integration
Project Structure



Overview
In modern data-driven applications and smart IOT systems, streaming data pipelines are essential for handling real-time data ingestion, processing, and storage.

In this context, comes our project which is a part of a bigger project to create a cutting edge IOT system that can mesure and notify users in real time about the variations of water sources quality.


In reality, the full project was composed of 3 main phases : A) Hardware part where a physical system was supposed to be put in place and from it we catch sensors data of water.
                                                             B) My actual contribution to the full project where a streaming data pipeline where needed to cmmunicated the sensed data, process it and display it into a dashboard
                                                             C) The creation of a large scale web application to handle the dashboarding of the streamed processed data.

This project showcases the B part of the project and as I worked separetly I needed to generate my own data which were gathered on an Excel file and that was the input of the pipeline so:

-Data is produced by a Python script from the rows of excel file  into Kafka topics.
-Consumer script  in Python configures Spark to  process incoming data in real-time.
-Avro is used for data backup or archiving.
-Processed data is stored in InfluxDB (time-series) and/or DynamoDB (NoSQL).


Architecture

![Capture d'écran 2025-02-18 160029](https://github.com/user-attachments/assets/2f6c84f9-4f45-416f-b2fe-6039662e2a31)


