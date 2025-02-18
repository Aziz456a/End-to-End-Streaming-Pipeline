# End-to-End-Streaming-Pipeline

This repository contains an end-to-end streaming data pipeline that leverages:

- Apache Kafka for message ingestion and queuing  
- Apache Spark for streaming data processing  
- Python (producers/consumers and utility scripts) used in Pycharm as an IDE  
- Avro for data serialization and backup  
- InfluxDB for time-series data storage  
- Amazon DynamoDB for Cloud High Availibility NoSQL data storage  

---

## Table of Contents:

- [Overview](#overview)  
- [Architecture](#architecture)  
- [Features](#features)  
---

## Overview

In modern data-driven applications and smart IOT systems, streaming data pipelines are essential for handling real-time data ingestion, processing, and storage.

In this context, comes our project which is a part of a bigger project to create a cutting edge IOT system that can mesure and notify users in real time about the variations of water sources quality.

In reality, the full project was composed of 3 main phases : &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
A) Hardware part where a physical system was supposed to be put in place and from it we catch sensors data of water.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;B) My actual contribution to the full project where a streaming data pipeline where needed to cmmunicated the sensed data, process it and display it into a dashboard  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;C) The creation of a large scale web application to handle the dashboarding of the streamed processed data.

This project showcases the B part of the project and as I worked separetly I needed to generate my own data which were gathered on an Excel file and that was the input of the pipeline so:

- Data is produced by a Python script from the rows of excel file into Kafka topics.  
- Consumer script in Python configures Spark to process incoming data in real-time.  
- Avro is used for data backup or archiving.  
- Processed data is stored in InfluxDB (time-series) and/or DynamoDB (NoSQL).

---

## Architecture

![Capture d'écran 2025-02-18 160029](https://github.com/user-attachments/assets/2f6c84f9-4f45-416f-b2fe-6039662e2a31)

As we can see in the architecture above, the pipeline can be described as:

- Raw Data is ingested from an excel file using the script (**producer.py**) which actually generates a pandas dataframe from the excel file raw data, loops over it and sends the records progressively to a Kafka topic. This step ensures that new data is continuously fed into the system.
- Kafka acts as a distributed messaging platform to receive and buffer data. In fact, Kafka buffers incoming data in a topic. Multiple consumers can subscribe to this topic to process data in parallel.
- Spark processes data in real-time (e.g., filtering, transformations, ...) and sends the results to Kafka again using the **consumer.py**script.
- Avro is used to efficiencly serialize the raw data and make a back up for it. The **avaro_test.py** script serializes the streaming data into Avro format for backup or archival. It behaves as a second consumer from the Kafka topics beside the Spark consumer. This ensures data can be restored or reprocessed if needed (e.g., compliance or historical analysis).
- InfluxDB stores processed data in a time-series database for analytics. This is handled using the script **influx_test.py**.
- DynamoDB (in AWS) stores processed data in a NoSQL store for real-time dashboards. In fact, the **cloud_amaz.py** uses a dedicated python client librairy to implement the logic of sending data to the DynamoDB instance.

---

## Features

- **Scalable** & **Fault-Tolerant** ingestion with Kafka.  
- **Real-Time Processing** using Python and Spark streaming.  
- **Flexible** Storage and **High Availibility**:  
      - InfluxDB for time-series data  
      - DynamoDB for fast NoSQL queries  
- **Data Archiving** and **reduddancy** with Avro format.  
- **Extensibility** to plug in other data sinks or sources.
