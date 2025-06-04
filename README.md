Walmart Sales Data ETL Pipeline on Google Cloud Platform
This repository contains an Apache Airflow DAG for orchestrating an end-to-end ETL pipeline
That processes Walmart sales data stored in Google Cloud Storage (GCS) and loads it into BigQuery for analysis and reporting.

The pipeline automates the extraction, transformation, and loading (ETL) of Walmart sales and merchant data:
Extract: Loads raw JSON sales and merchant data files from GCS.
Transform: Performs data cleansing and enrichment by merging sales with merchant information.
Load: Inserts the processed and enriched data into a target BigQuery table, supporting incremental updates with merge (upsert) logic.

Dataset and Table Creation: Automatically creates BigQuery datasets and tables if they do not exist.
Data Loading from GCS to BigQuery: Loads newline-delimited JSON files into staging tables.
Upsert Logic with BigQuery MERGE: Updates existing records and inserts new records in the target table, ensuring data consistency.
Modular and Scalable DAG: Organized task groups for better readability and maintenance.
Cloud Composer Compatible: Designed to run on Google Cloud Composer with Google-managed Airflow.

Architecture Components:
BigQueryCreateEmptyDatasetOperator: Creates the BigQuery dataset.
BigQueryCreateEmptyTableOperator: Defines and creates tables with explicit schemas.
GCSToBigQueryOperator: Loads data from GCS into staging tables.
BigQueryInsertJobOperator: Executes SQL MERGE queries for incremental data upsertion.
Airflow DAG and TaskGroup: Orchestrates and groups tasks to form a coherent pipeline.
