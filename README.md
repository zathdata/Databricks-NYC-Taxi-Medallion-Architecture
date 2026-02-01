# Databricks NYC Taxi Medallion Architecture Practice Project

This project has an end-to-end ETL pipeline using the NYC Yellow Taxi dataset. I implemented using Medallion Architecture within Databricks Free Edition to transform raw Parquet/CSV data into BI ready data.

## Project Overview
* **Environment:** Databricks Free Edition
* **Storage:** Unity Catalog Volumes and Delta Tables
* **Dataset:** 4 months of NYC Yellow Taxi Trip Records (2025)

## Data resources
* Go to the NYC Taxi Trips [Website](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page/)
* Download the Zone Look UP csv file and the Yellow Taxi 2025 parquet files

## Medallion Architecture
**Bronze Layer:** We will read the data in the catalog, add `ingestion_time` and `_source_file` columns, leaving the data raw, and finally writing as a delta table.

**Silver Layer:** Load the data from the bronze layer, do an exploratory data analysis, clean the data and write the table in delta format in the silver schema.

**Gold Layer:** Load the data from the silver layer, create new aggregate columns, rename columns for accessibility, create dimension tables if needed and make data ready for BI.

## How to Run
1. **Catalog Setup:** Run `setup_catalog.ipynb` to initialize the `nyc_yellow_taxi` catalog
1. **Data Import:** Upload the NYC Parquet files into the Databricks Volume
1. **Execute Notebooks:** Run bronze.ipynb, silver.ipynb, and gold.ipynb in order
