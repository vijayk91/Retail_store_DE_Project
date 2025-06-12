🛠️ End-to-End Data Engineering Project: Retail Analytics using ADF, Spark, Synapse & ADLS

📌 Project Objective
Retail clients need a daily report showing:
🛒 Total Purchase
💰 Total Revenue

To fulfill this, we use a Medallion Architecture leveraging Azure services.

🚀 Architecture Overview

⚙️ Tools & Technologies Used
| Service                                          | Purpose                                        |
| ------------------------------------------------ | ---------------------------------------------- |
| **Azure Data Factory (ADF)**                     | Data orchestration and ingestion from REST API |
| **Azure Data Lake Storage (ADLS)**               | Raw and processed data storage                 |
| **Apache Spark (Databricks/Synapse Spark Pool)** | Data transformation                            |
| **Azure Synapse Analytics**                      | Data aggregation & reporting                   |


🧱 Medallion Architecture
The architecture consists of three layers:

🥉 Bronze Layer
Ingest raw data from REST API
Store it as-is into ADLS using ADF

🥈 Silver Layer
Use Spark (Synapse/Databricks) to:
Cleanse the data
Create structured datasets
Save as Parquet format in ADLS

📌 Actions:
Remove nulls, fix types
Standardize column names
Create "purchase" dataset

🥇 Gold Layer
Use Spark SQL or Synapse SQL Pool to:
Generate aggregated reports (Total Purchase & Revenue)
Create SQL views/tables for easy client access

📌 Outputs:sql
SELECT SUM(amount) AS total_revenue, COUNT(*) AS total_purchases
FROM gold_dataset
WHERE CAST(timestamp AS DATE) = CURRENT_DATE
