# Retail_sales_end_to-_end_data_pipeline_proj-
DATA PIPELINE USING DELTA LAKE AND PYSPARK


🎯 Objective

This project simulates a retail data engineering pipeline using open-source tools like PySpark and Delta Lake, fully implemented in Google Colab. The goal is to demonstrate data integration, transformation, storage optimization, and quality monitoring in a cloud-like environment — without using Microsoft Azure or Databricks.

## 🧭 Overview

Retail companies often need to analyze sales transactions and product metadata for operational and strategic insights. This project builds a scalable ETL pipeline to:

- Ingest transaction and product datasets
- Clean, validate, and transform the data
- Join and enrich the datasets
- Store the results as Delta Tables
- Optimize storage and monitor data quality

We use PySpark and Delta Lake in Google Colab to simulate features similar to Azure Data Factory, ADLS Gen2, and Databricks — all without leaving the notebook environment.

---

## ⚙️ ETL Process

This pipeline processes structured CSV data using PySpark DataFrames. The process is modular and can be run incrementally or scheduled with Colab/cron jobs.

### 🔹 Source Data

The datasets are stored in the `data/` folder and include:

- `transactions.csv`: Transaction-level retail sales data
- `products.csv`: Metadata for each product sold

### 🔄 Extraction

Data is ingested from two source CSV files:

transactions.csv: Contains raw retail transaction records.

products.csv: Contains product catalog data.

These files are read into PySpark DataFrames using spark.read.csv() with headers and inferred schema. They are stored in the data/ directory within the project for easy access and version control.


### 🔧 Transformation

1. **Schema validation and null checks**
2. **Join**: Transactions enriched with product metadata
3. **Metrics calculation**: Revenue, average spend per product
4. **Outlier removal**: Based on configurable thresholds
5. **Data quality checks**: Missing values, invalid rows

### 💾 Load

- The cleaned and transformed data is saved in **Delta Lake format**
- Data is stored locally (in Colab environment) or optionally to Google Drive
- Delta tables are partitioned for performance

### 🪄 Optimization

- Delta table compaction and file optimization
- Metadata handling and Z-Ordering simulation (optional)

### 🔍 Monitoring

Maintaining data quality and integrity is essential in any ETL pipeline. This project integrates basic but critical data quality monitoring steps within the transformation phase and documents them in logs and summary outputs

📊 Monitoring Output
Log summaries printed at each stage of transformation (total rows, dropped rows, null counts, duplicates removed)

Delta Lake history allows time-travel and audit logs

Metrics summary displayed after transformations:

Valid records count

Records dropped by type (nulls, outliers, duplicates)

Transformation duration

🧼 Optional Enhancements
If needed, the following tools and techniques can be integrated:

Great Expectations for robust, testable validation

Delta Table Versioning and Time Travel for rollback and auditing

Custom Logging with Python’s logging module for persistent logs



---

## File Structure

```bash
.
├── README/data/
│   ├── transactions.csv
│   └── products.csv
├── notebooks/
│   ├── 01_load_data.ipynb
│   ├── 02_transform_data.ipynb
│   ├── 03_store_delta.ipynb
│   ├── 04_optimize_storage.ipynb
│   └── 05_monitor_quality.ipynb
├── utils.py
├── requirements.txt
└── README.md



