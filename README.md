# 📊 Sales Data Warehouse | Medallion Architecture (SQL Server)

## Overview
This project builds a modern data warehouse from raw ERP and CRM source data, following the **Medallion Architecture** pattern (Bronze → Silver → Gold), then uses the final model to perform exploratory data analysis (EDA) and answer real business questions.

The goal was to simulate an end-to-end data pipeline the way it would exist in a real company — from messy raw data, through cleaning and standardization, to a business-ready star schema used for analysis and reporting.

---

## 🏗️ Architecture

**Bronze Layer** — Raw data, loaded as-is from source CSV files (ERP & CRM -style customer, product, and sales data) via `BULK INSERT`. No transformations applied — this layer preserves an exact copy of the source for traceability.

**Silver Layer** — Cleaned and standardized data. A few actions done are:
- Removing duplicates (using `ROW_NUMBER()` to keep the most recent/valid record)
- Standardizing categorical values (e.g., gender, marital status)
- Handling missing values (`COALESCE`)
- Deriving historical date ranges (e.g., `LEAD()` for start/end date tracking)
- Trimming and correcting inconsistent formatting

**Gold Layer** — Business-ready star schema, built as views on top of Silver:
- `gold.dim_customers`
- `gold.dim_products`
- `gold.fact_sales`

This is also where data modeling, EDA, and business analysis all took place — including foreign key integrity checks to validate the fact-to-dimension relationships before trusting the model for analysis.

---

## 🛠️ Tools & Skills Used
- **SQL Server / T-SQL** — schema design, stored procedures, window functions, CTEs
- **Medallion Architecture** — Bronze / Silver / Gold data modeling
- **Star Schema Design** — fact and dimension table modeling
- **Data Cleaning** — deduplication, standardization, null handling
- **EDA & Business Analysis** — trend analysis, segmentation, KPI calculation

---

## 📈 A Few Key Analysis Performed
- Sales Performance
- Monthly sales trends (running totals & moving averages)
- Category Distribution in overall sales
- Customer Segmentation
- Product performance aggregation (total sales, total orders, average selling price)


---

## 📂 Repository Structure
```
├── datasets/
│   ├── source_crm/          -- Raw CRM source files
│   └── source_erp/          -- Raw ERP source files
├── docs/
│   ├── data_flow_diagram.png
│   ├── data_integration.png
│   ├── data_model_diagram.png
│   └── etl_pipeline_overview.png
├── scripts/
│   ├── bronze/               -- Raw data load scripts
│   ├── silver/                -- Cleaning & transformation scripts
│   ├── gold/                 -- Star schema views
│   ├── analysis/            -- Business question / analysis scripts
│   └── eda/                   -- Exploratory data analysis scripts
├── tests/
├── LICENSE
└── README.md
```

---

## 🔍 What This Project Demonstrates
- Ability to design and implement a layered data warehouse from scratch
- Understanding of data quality, grain, and referential integrity
- Translating business questions into SQL logic
- Building analysis-ready models rather than working from pre-cleaned datasets

---

## 🚀 Let's Connect
I'm actively building my portfolio as I transition into a Data Analyst role, with a focus on **e-commerce and sales analytics**. If you'd like to connect, share feedback, or discuss opportunities, feel free to reach out on LinkedIn:

**🔗 [Connect with me on LinkedIn](https://www.linkedin.com/in/deborah-obasi-47b0751a4/)**


---

🙏 Acknowledgment

A huge thanks to Baraa for the guidance and teaching style that shaped how I approached this project. The clarity and structure behind the Medallion Architecture concepts taught made this build possible, and I'm grateful for the foundation it gave me as I continue growing in data analytics and engineering.
