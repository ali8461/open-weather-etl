
# 🌦️ Weather ETL Pipeline using AWS (S3, Glue, Redshift, Airflow)

This project implements an end-to-end ETL pipeline that extracts 5-day weather forecast data from the **OpenWeather API**, processes it using **AWS Glue**, and loads it into an **Amazon Redshift** data warehouse. The pipeline orchestration is handled by **Amazon Managed Apache Airflow**, and the infrastructure is provisioned via **AWS CloudFormation**.

### Architecture Diagram

![ETL Architecture](resources/Architecture.png)

## 🛠️ Architecture Overview

```
OpenWeather API → Python (ETL Script) → S3 Bucket → AWS Glue → Amazon Redshift
                                 ↳ Orchestrated by Apache Airflow (Managed)
```

### Components:
- **Data Source**: OpenWeather 5-Day Forecast API.
- **Storage**: Amazon S3 (Raw and Transformed data).
- **Transformation**: AWS Glue Job (ETL transformation).
- **Data Warehouse**: Amazon Redshift.
- **Orchestration**: Amazon Managed Apache Airflow (MWAA).
- **Infrastructure as Code**: AWS CloudFormation.

## 📂 Repository Structure

```
├── dags/
│ ├── openweather_api.py # Airflow DAG definition to extract weather data
│ ├── transform_redshift_load.py # Airflow DAG for transform and load to Redshift
├── scripts/
│ └── transform.py # Python script to transform data
├── resources/
│ ├── architecture.png # Architecture diagram
│ └── requirements.txt # Python dependencies for Airflow and project
├── infrastructure.yaml # CloudFormation template for AWS resources
├── README.md # Main project documentation

```

## ⚙️ Setup Instructions

### Prerequisites:
- AWS Account with access to S3, Glue, Redshift, CloudFormation, and Managed Airflow (MWAA).
- OpenWeather API Key.
- Python 3.x.
- AWS CLI configured with necessary permissions.

### Steps:
1. **Clone the Repository:**
    ```bash
    git clone https://github.com/yourusername/weather-etl-pipeline.git
    cd weather-etl-pipeline
    ```

2. **Deploy Infrastructure using CloudFormation
   

3. **Upload DAG and Scripts to S3 Bucket
   

4. **Configure Airflow Environment
details.

5. **Activate Airflow DAG   

## 🚀 Workflow Steps

1. **Extract**: Fetch weather data from OpenWeather API using Python.
2. **Load to S3**: Store raw data in S3 bucket (CSV/JSON format).
3. **Transform (Glue Job)**: Clean and transform data as per Redshift schema.
4. **Load to Redshift**: Insert transformed data into Redshift cluster.
5. **Orchestration**: Airflow handles task sequencing, retries, and monitoring.

## 📝 Airflow DAG Flow
- `extract_weather_data`: PythonOperator to fetch and store data to S3.
- `run_glue_job`: Trigger AWS Glue job for data transformation.
- `load_to_redshift`: Task to load data into Redshift using COPY command.
- Dependencies defined to ensure sequential execution.

## 📊 Monitoring & Logs
- **Airflow UI**: DAG Runs, Task Logs, Monitoring.
- **AWS CloudWatch**: Logs for Glue Jobs and Redshift Activities.
- **S3**: Data at each stage (Raw → Processed).
