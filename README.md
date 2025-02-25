# Assesing Climate Trends Using Google Cloud Platform
his project demonstrates a complete data pipeline on Google Cloud Platform (GCP), from data ingestion to visualization. It utilizes Google Cloud Storage (GCS) for data ingestion, Cloud Data Fusion for ETL processing, BigQuery for data analysis, and Looker Studio for interactive visualization. The project focuses on analyzing climate change datasets to extract meaningful insights

# Google Cloud Data Pipeline for Climate Analysis  

## 📌 Overview  
This project implements a **data pipeline on Google Cloud Platform (GCP)** to process and analyze climate change datasets. The pipeline follows a structured data lifecycle, including:  
1. **Data Ingestion** – Google Cloud Storage (GCS) for raw data storage.  
2. **Data Pre-Processing** – Cloud Data Fusion for ETL (Extract, Transform, Load) operations.  
3. **Data Analysis** – BigQuery for querying and analyzing structured data.  
4. **Data Visualization** – Looker Studio for interactive dashboards and insights.  

## 🚀 Technologies Used  
- **Google Cloud Storage (GCS)** – Secure cloud storage for raw datasets.  
- **Cloud Data Fusion** – ETL pipeline creation for data transformation.  
- **BigQuery** – High-performance data warehouse for querying large datasets.  
- **Looker Studio** – Interactive data visualization and dashboarding tool.  

## 🛠️ Implementation Steps  

### **1. Data Ingestion**  
- Created a **Google Cloud Storage (GCS) bucket** for storing raw climate datasets.  
- Uploaded the dataset (`climate-change-dataset.csv`) to the GCS bucket.  
- Verified data availability using:  
  ```bash
  gsutil ls gs://bkt-bdaa
  ```
### 2. Data Pre-Processing (ETL with Cloud Data Fusion)
- Configured a Cloud Data Fusion instance to design an ETL pipeline.
- Selected GCS as the data source and applied transformations using Data Wrangler.
- Loaded the cleaned dataset into BigQuery.
- Deployed and ran the ETL pipeline.
### 3. Data Analysis with BigQuery
- Created a dataset and table in BigQuery:
```sql
CREATE TABLE `bdaa-g13-project.climatechange.cc_data` AS
SELECT * FROM `bkt-bdaa.climate-change-dataset`;
```
- Executed SQL queries to derive insights, such as:

#### 3.1 Average Temperature by Year
```sql
SELECT year, AVG(temperature) AS avg_temp
FROM `bdaa-g13-project.climatechange.cc_data`
GROUP BY year
ORDER BY year;
```
#### 3.2 Top 10 Countries with the Highest CO2 Emissions
```sql
SELECT country, SUM(co2_emissions) AS total_emissions
FROM `bdaa-g13-project.climatechange.cc_data`
GROUP BY country
ORDER BY total_emissions DESC
LIMIT 10;
```

### 4. Data Visualization with Looker Studio
- Connected Looker Studio to BigQuery for real-time data visualization.
- Created interactive line charts, geo maps, and pie charts to visualize temperature changes, CO2 emissions, and extreme weather events.

### 📊 Example Insights
🔹 Global Average Temperature Over Time:
Shows a clear upward trend in temperatures, indicating climate change impact.
🔹 CO2 Emissions by Country:
Identifies the top polluters, aiding in policy decisions and environmental strategies.
🔹 Sea Level Rise vs. Extreme Weather Events:
Analyzes the correlation between rising sea levels and severe weather occurrences.

### 📂 Repository Structure
```
/data             # Sample climate dataset  
/sql_queries      # BigQuery SQL scripts  
/visualizations   # Looker Studio dashboard screenshots  
README.md        # Project documentation
```
### 📌 Key Learning Outcomes
-  Building end-to-end data pipelines on Google Cloud Platform (GCP)
-  Performing ETL processing using Cloud Data Fusion
-  Running SQL-based analytics on BigQuery
-  Creating interactive data visualizations with Looker Studio

