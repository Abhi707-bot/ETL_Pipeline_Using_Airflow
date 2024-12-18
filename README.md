# ETL_Pipeline_Using_Airflow

# Amazon Book ETL Pipeline with Apache Airflow, Docker, and PostgreSQL

This project implements an ETL (Extract, Transform, Load) pipeline to scrape Amazon book data, process it using Python, and store it in a PostgreSQL database. The entire pipeline is orchestrated using **Apache Airflow** and the web scraping is performed inside a **Docker** container.

## Project Overview

The ETL pipeline involves the following steps:

1. **Extract (E):** Scrape book data (title, author, price, link) from Amazon's website using a Dockerized Python script.
2. **Transform (T):** Process the scraped data (e.g., clean prices, handle missing values) using Python.
3. **Load (L):** Load the transformed data into a PostgreSQL database.

This pipeline is orchestrated using **Apache Airflow**, which automates and monitors the entire process.

![Blank diagram (1)](https://github.com/user-attachments/assets/2ab16a5d-0087-4ae0-803e-9afd1d7d12c4)


## Workflow Overview

### 1. **Extract Data (Scrape Amazon)**
   - **Docker Container:** A Python script running inside a Docker container scrapes book details from Amazon.
   - **Data Scraping:** The script retrieves information such as book titles, authors, prices, and links.
   - **Output:** Scraped data is saved as a CSV file.

![image4](https://github.com/user-attachments/assets/19b5552d-96d3-4125-942b-157fe3e7a9e4)


### 2. **Transform Data (Process with Python)**
   - **Data Processing:** The extracted data is cleaned using Python. This includes tasks such as:
     - Removing currency symbols and commas from price fields.
     - Handling missing or null values.
   - **Output:** Transformed data is saved in a new CSV file.

### 3. **Load Data into PostgreSQL**
   - **PostgreSQL Insertion:** The transformed data is inserted into a PostgreSQL database, specifically into the `books` table.
   - **Connection:** The `psycopg2` library is used to connect to PostgreSQL and load the data.

![image3](https://github.com/user-attachments/assets/93f20ece-d913-43fc-b1a4-0c688e3599c2)


### 4. **Orchestrate with Apache Airflow**
   - **Airflow DAG:** An Apache Airflow Directed Acyclic Graph (DAG) manages the ETL process. The tasks are:
     - **DockerOperator**: Runs the Docker container for scraping.
     - **PythonOperator**: Handles data transformation.
     - **PostgresOperator**: Loads the data into PostgreSQL.
   - **Airflow UI:** You can monitor and control the execution of the DAG via the Airflow Web UI at `http://localhost:8080`.

![image1](https://github.com/user-attachments/assets/60860aaf-e79a-437a-9af9-3ae6b248a5f0)

![image2](https://github.com/user-attachments/assets/9bff3749-39f7-43e1-9a72-63af68c9ad12)

![image5](https://github.com/user-attachments/assets/d221008f-aa31-4270-b6e8-350a755f79cd)


## Setup Instructions

### Prerequisites

- **Docker** - To run the Python script in a container.
- **Apache Airflow** - To orchestrate the ETL pipeline.
- **PostgreSQL** - Running locally on `localhost`.
- **Python 3.x** - Required for transformation logic.


  