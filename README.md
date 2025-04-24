# Live-Streaming-Data-Pipeline-with-Docker-Apache-NiFi-AWS-S3-and-Snowflake
## Project Overview:
This project demonstrates a real-time data pipeline using Dockerized environments, live data generation in Python, and seamless automation through Snowflake Tasks and Streams all orchestrated with Apache NiFi.The entire Docker-based environment (Apache NiFi, Jupyter Notebook, etc.) was set up and executed on an AWS EC2 instance. This provides a scalable and cost-effective solution for running our data streaming pipeline.


## Architecture:
<img src="https://github.com/Bhargav-data-driven/Live-Streaming-Data-Pipeline-with-Docker-Apache-NiFi-AWS-S3-and-Snowflake/blob/main/live%20stream.jpg" width="850" height="500">

## Tech Stack:
- Amazon EC2 For Docker-based environment (Apache NiFi, Jupyter Notebook, etc.)
- Docker: For environment setup (Jupyter Notebook, Apache NiFi, Zookeeper)
- Apache NiFi: For real-time data integration and automation
- Python (Jupyter Notebook): To simulate live data generation
- AWS S3: For storing raw and transformed data
- Snowpipe: To automatically ingest S3 data into Snowflake
- Snowflake Streams & Tasks: To manage incremental loads and automate Slowly Changing Dimensions (SCD1 & SCD2)

## Data Flow:
**1. Amazon EC2** Hosts the Docker environment.

**2. Python Jupyter Notebook** (running in Docker) generates streaming customer data.

**3. Apache NiFi** (also in Docker) picks up this data and pushes it to **AWS S3**.

**4. Snowpipe** automatically ingests the raw data from S3 into a **Staging Table** in Snowflake.

**5. A Snowflake Stream** captures changes from the staging table.

**6. A Snowflake Task** automates applying the changes to Target Tables (SCD1 and SCD2 logic applied).

**7.** Final tables hold the latest and historical view of customer data.

## Key Features:
- No paid third-party tools used — 100% open-source or free-tier.
- Full automation using NiFi, Snowflake Tasks, and Streams.
- Reproducible with Docker – no local installations required.
- Clean handling of data updates using SCD Type 1 & 2.
- Production-ready data pipeline setup.

## How to Run:
1. Clone the repo.

2. Start Docker containers (docker-compose up). ([Docker setup](https://github.com/Bhargav-data-driven/Live-Streaming-Data-Pipeline-with-Docker-Apache-NiFi-AWS-S3-and-Snowflake/blob/main/commands))

3. Access Jupyter to run the data generator. ( [data genration file](https://github.com/Bhargav-data-driven/Live-Streaming-Data-Pipeline-with-Docker-Apache-NiFi-AWS-S3-and-Snowflake/blob/main/faker.ipynb).)
 
4. Let NiFi take over to automate flow → S3 → Snowflake. ([Nifi workflow](https://github.com/Bhargav-data-driven/Live-Streaming-Data-Pipeline-with-Docker-Apache-NiFi-AWS-S3-and-Snowflake/blob/main/nifi%20setup.jpg))
