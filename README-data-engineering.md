# Retail ETL Pipeline & Power BI Dashboard

Data Engineering project — building a full ETL pipeline for retail sales data and visualizing it through an interactive Power BI dashboard.

## Overview

This project takes a raw retail sales dataset and transforms it into a structured data warehouse, then surfaces key business metrics through a Power BI dashboard. The pipeline was built using Pentaho Data Integration (Spoon), with MySQL as the target database.

## Dataset

- Retail store sales dataset (`retail_store_sales.csv`), 12,575 rows

## Pipeline architecture

The pipeline transforms the raw dataset into a **star schema** warehouse (`retail_db`):

- **Fact table:** `fact_table` — core sales transactions
- **Dimension tables:** `dim_customer`, `dim_date`, `dim_location`, `dim_payment`, `dim_product`
- Data cleaning handled via `cleaning_sales.ktr` before loading into the warehouse
- Orchestrated end-to-end through `retail_pipeline.ktr` and `retail_pipeline_job.kjb`

## Challenges & fixes

- Recovered the database from an InnoDB corruption caused by a MySQL crash mid-project, without losing pipeline progress

## Dashboard

Built in Power BI, the dashboard includes:
- KPI cards for key sales metrics
- Revenue breakdowns
- Time-series visualizations of sales trends

See `dashboard/` for the `.pbix` file and dashboard screenshots.

## Repository structure

```
├── etl/
│   ├── cleaning_sales.ktr
│   ├── dim_customer.ktr
│   ├── dim_date.ktr
│   ├── dim_location.ktr
│   ├── dim_payment.ktr
│   ├── dim_product.ktr
│   ├── fact_table.ktr
│   ├── retail_pipeline.ktr
│   └── retail_pipeline_job.kjb
├── database/
│   └── retail_db.sql
├── dashboard/
│   ├── RetailDashboard.pbix
│   └── screenshots/
├── docs/
│   └── data-engineering-presentation.pdf
└── README.md
```

## Tools & technologies

- Pentaho Data Integration (Spoon) — ETL
- MySQL — data warehouse
- Power BI — dashboarding and visualization

## Context

Prepared as part of a Data Engineering course project at BINUS University.
