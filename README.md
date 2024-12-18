# ETL_Pipeline_Using_Airflow

# Amazon Book ETL Pipeline with Apache Airflow, Docker, and PostgreSQL

This project implements an ETL (Extract, Transform, Load) pipeline to scrape Amazon book data, process it using Python, and store it in a PostgreSQL database. The entire pipeline is orchestrated using **Apache Airflow** and the web scraping is performed inside a **Docker** container.

## Project Overview

The ETL pipeline involves the following steps:

1. **Extract (E):** Scrape book data (title, author, price, link) from Amazon's website using a Dockerized Python script.
2. **Transform (T):** Process the scraped data (e.g., clean prices, handle missing values) using Python.
3. **Load (L):** Load the transformed data into a PostgreSQL database.

This pipeline is orchestrated using **Apache Airflow**, which automates and monitors the entire process.

![Blank diagram (1).png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/5c60b8e0-b0c6-4c9d-a0ab-e9ed13e8b18e/Blank_diagram_(1).png)

## Workflow Overview

### 1. **Extract Data (Scrape Amazon)**
   - **Docker Container:** A Python script running inside a Docker container scrapes book details from Amazon.
   - **Data Scraping:** The script retrieves information such as book titles, authors, prices, and links.
   - **Output:** Scraped data is saved as a CSV file.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/10aba727-d361-4737-843f-68bc67d3d9ba/image.png)

### 2. **Transform Data (Process with Python)**
   - **Data Processing:** The extracted data is cleaned using Python. This includes tasks such as:
     - Removing currency symbols and commas from price fields.
     - Handling missing or null values.
   - **Output:** Transformed data is saved in a new CSV file.

### 3. **Load Data into PostgreSQL**
   - **PostgreSQL Insertion:** The transformed data is inserted into a PostgreSQL database, specifically into the `books` table.
   - **Connection:** The `psycopg2` library is used to connect to PostgreSQL and load the data.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/d0bb4b1c-14c8-4442-b62d-a3129d2a1305/image.png)

### 4. **Orchestrate with Apache Airflow**
   - **Airflow DAG:** An Apache Airflow Directed Acyclic Graph (DAG) manages the ETL process. The tasks are:
     - **DockerOperator**: Runs the Docker container for scraping.
     - **PythonOperator**: Handles data transformation.
     - **PostgresOperator**: Loads the data into PostgreSQL.
   - **Airflow UI:** You can monitor and control the execution of the DAG via the Airflow Web UI at `http://localhost:8080`.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/7abdf90c-1525-4f48-b381-43fa7cdf6c15/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/3ce45275-66ba-4414-8e80-24acd52928ef/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/95e75144-f956-4e60-bea7-299d210aa570/1528f817-07b8-4395-a4f2-4603f3b63d80/image.png)

## Setup Instructions

### Prerequisites

- **Docker** - To run the Python script in a container.
- **Apache Airflow** - To orchestrate the ETL pipeline.
- **PostgreSQL** - Running locally on `localhost`.
- **Python 3.x** - Required for transformation logic.


  
