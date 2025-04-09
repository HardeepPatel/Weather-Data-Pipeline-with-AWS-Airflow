# 🌦️ Weather Data Pipeline with AWS & Airflow

This project demonstrates the design and implementation of a scalable, cloud-native data pipeline to ingest and analyze real-time weather data using **Apache Airflow**, **AWS services**, **Python**, and **Apache Spark**. The pipeline extracts weather data from the OpenWeather API, stores it in **Amazon S3**, transforms it using **AWS Glue**, and loads it into **Amazon Redshift** for analytics.

---

## 🏗️ High-Level Architecture

![Weather Pipeline Architecture](https://github.com/user-attachments/assets/00268a61-4725-49b2-a3d0-a11aa9213521)

The architecture is deployed using **Infrastructure as Code (IaC)**, ensuring repeatability, scalability, and ease of management. The pipeline is orchestrated through two distinct **Apache Airflow DAGs**.

---

## ⚙️ DAG 1: Data Ingestion (OpenWeather → S3)

This DAG is responsible for fetching and storing the weather data.

### 🔹 Task 1: Extract Weather Data from OpenWeather API  
- Utilizes Airflow's `PythonOperator`.  
- Uses the `requests` library to fetch current weather data.  
- Parses the response and structures it into a clean DataFrame.

### 🔹 Task 2: Store Data in Amazon S3  
- Uses `S3CreateObjectOperator` to upload the structured data into an S3 bucket.  
- Data is stored in a partitioned format for optimized downstream querying.

---

## ⚙️ DAG 2: Data Transformation & Loading (S3 → Redshift)

This DAG handles transformation and loading of the data into Redshift.

### 🔹 Task 1: Sensor to Check DAG 1 Completion  
- Ensures that DAG 1 has successfully completed before starting downstream operations.

### 🔹 Task 2: ETL Processing with AWS Glue  
- Leverages `GlueContext` and `SparkContext` to perform transformations on raw weather data.  
- Transformed data is then loaded into **Amazon Redshift** using Redshift-compatible formats.

---

## ✅ Key Features

- 🔁 **Automated Workflows:** Fully orchestrated via Apache Airflow.  
- ☁️ **Cloud-Native Infrastructure:** Built using AWS Glue, S3, and Redshift.  
- 🧾 **Scalable Architecture:** Easily extendable to ingest multiple data sources.  
- 🧱 **Infrastructure as Code (IaC):** Deployed using Terraform / CloudFormation templates.  
- 🧪 **Data Quality Controls:** Built-in validation and logging for reliable operations.

---

## 📊 Use Cases

- Real-time weather monitoring & alerting  
- Historical weather trend analysis  
- Integration with BI dashboards for reporting  
- Scalable ETL foundation for external data sources  

---

## 🔚 Conclusion

This project showcases a full-stack, cloud-native data pipeline capable of ingesting, processing, and visualizing real-time weather data. By integrating **Apache Airflow** with **AWS services**, the system ensures automation, scalability, and reliability—making it a strong foundation for modern data engineering workflows.

---
