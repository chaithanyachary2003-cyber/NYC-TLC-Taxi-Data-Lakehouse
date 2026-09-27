# NYC TLC Taxi Data Lakehouse

An end-to-end Data Engineering project built using **Databricks, PySpark, Delta Lake, Unity Catalog, SQL, and Databricks Workflows**.

This project demonstrates how raw NYC Taxi & Limousine Commission (TLC) trip data can be transformed into clean, validated, and business-ready datasets using a **Medallion Architecture**.

---

## 📌 Project Overview

The goal of this project is to build a scalable lakehouse pipeline for NYC taxi trip data.

The pipeline follows a three-layer Medallion Architecture:

**Bronze → Silver → Gold**

- **Bronze:** Raw source data
- **Silver:** Cleaned and standardized data
- **Gold:** Business-ready analytical datasets

The project also uses **Unity Catalog** for data organization and **Databricks Workflows** for ETL orchestration and scheduling.

---

## 🏗️ Architecture

```text
                    NYC TLC Taxi Data
                           │
                           ▼
                 ┌──────────────────┐
                 │      BRONZE      │
                 │   Raw Delta Data │
                 │    50,000 rows   │
                 └────────┬─────────┘
                          │
                          │ PySpark
                          │ Data Cleaning
                          │ Type Conversion
                          ▼
                 ┌──────────────────┐
                 │      SILVER      │
                 │  Cleaned Data    │
                 │   49,503 rows    │
                 └────────┬─────────┘
                          │
                          │ Business
                          │ Aggregations
                          ▼
                 ┌──────────────────┐
                 │       GOLD       │
                 │ Business-Ready   │
                 │    Analytics     │
                 └────────┬─────────┘
                          │
              ┌───────────┼───────────┐
              ▼           ▼           ▼
           Daily       Payment     Peak Hour
        Performance    Analysis     Analysis