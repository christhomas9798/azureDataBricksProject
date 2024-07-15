# formula1-azureDataBricks-project

# Azure Databricks Project: Formula One Race Data Analysis

## Project Overview
In this project, we built a Data Lake in Azure by ingesting Formula One race data from ergast.com. The project involved data ingestion, transformation, analysis, and presentation using Azure Databricks, Azure Data Factory (ADF), Azure Data Lake Storage Gen2 (ADLS), Delta Lake, and Power BI. The goal was to create a scalable solution following the Data Lakehouse architecture with Delta Lake, enabling in-depth analysis and BI reporting.

## Tools Used
- Python
- PySpark
- Azure Databricks
- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2 (ADLS)
- Delta Lake
- Power BI

## Data Source
The data for all the Formula One races from 1950 onwards is obtained from an open-source API called Ergast Developer API. The structure of the database is shown in the following ER Diagram and explained in the [Database User Guide](http://ergast.com/docs/f1db_user_guide.txt).

![ER Diagram](http://ergast.com/images/ergast_db.png)

## Key Steps

### Setup
- **Azure Subscription and Databricks Workspace:**
  - Created an Azure subscription and set up a Databricks workspace.
- **Compute Cluster:**
  - Created a compute cluster in Databricks for running queries and Python code.
- **Storage Account:**
  - Established an Azure Data Lake Storage Gen2 account with containers for demo, raw, processed, and presentation data.
- **Service Principals and Credentials Management:**
  - Created service principals to enable Databricks to access Azure Storage Lake.
  - Stored credentials securely in Azure Vault.
  - Set up and linked secrets in Databricks to access the credentials stored in the Azure Vault securely.

### Data Handling
- **Data Ingestion:**
  - Ingested raw CSV and JSON files from ergast.com into the raw container.
- **Data Transformation:**
  - Transformed the data by renaming columns, adding new columns (including an ingestion date column to track when the data was added), and converting the data to Delta format.
  - Stored the transformed data in the processed container, utilizing Databricks' Data Lakehouse architecture.

### Analysis and Visualization
- Analyzed the processed data to produce insights, such as race results with driver and constructor details, and identified dominance trends over the years.
- Created dashboards to visualize these findings, highlighting driver and constructor dominance.

### Automation and Optimization
- **Pipeline Creation:**
  - Used Azure Data Factory (ADF) to create pipelines for data ingestion, transformation, and other processes using Databricks notebooks.
- **Scheduling and Triggering:**
  - Set up triggers to automate pipeline runs on a weekly basis.
- **Merge Command Implementation:**
  - Implemented merge commands in Databricks notebooks to ensure the pipeline is compatible with weekly runs. The merge commands were designed to overwrite existing data if present and insert new data if available, without removing existing data.
- **Partitioning:**
  - Created partitions on the Delta format tables to facilitate efficient data handling and querying.

## Outcome
- Developed a comprehensive data solution following the Data Lakehouse architecture with Delta Lake.
- Conducted in-depth analysis of Formula One race data from 1950 onwards, identifying dominant drivers and teams.
- Enabled trend analysis and BI reporting through Power BI, facilitating data-driven insights and visualizations.
- Established a robust and scalable data pipeline that automates data processing and ensures up-to-date information is available for analysis and reporting.
