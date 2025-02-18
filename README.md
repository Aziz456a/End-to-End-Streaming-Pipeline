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
- [Prerequisites](#prerequisites)  
- [Installation & Setup](#installation--setup)  
  1. [Clone the Repository](#1-clone-the-repository)  
  2. [Install Dependencies](#2-install-dependencies)  
  3. [Set Up Kafka](#3-set-up-kafka)  
  4. [Set Up Spark](#4-set-up-spark)  
  5. [Set Up InfluxDB](#5-set-up-influxdb)  
  6. [Set Up DynamoDB](#6-set-up-dynamodb)  
  7. [Configure Environment Variables](#7-configure-environment-variables)  
- [Usage](#usage)  
  - [Producer](#producer)  
  - [Consumer](#consumer)  
  - [Avro Backup](#avro-backup)  
  - [Influx Testing](#influx-testing)  
  - [Spark Integration](#spark-integration)  
- [Project Structure](#project-structure)  

---

## Overview

In modern data-driven applications and smart IOT systems, streaming data pipelines are essential for handling real-time data ingestion, processing, and storage.

In this context, comes our project which is a part of a bigger project to create a cutting edge IOT system that can mesure and notify users in real time about the variations of water sources quality.

In reality, the full project was composed of 3 main phases : A) Hardware part where a physical system was supposed to be put in place and from it we catch sensors data of water.  
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

As we can see in the archit
