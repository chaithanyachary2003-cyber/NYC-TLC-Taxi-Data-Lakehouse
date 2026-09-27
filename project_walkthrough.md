# NYC TLC Taxi Data Lakehouse - Project Walkthrough

## 1. Source Data

NYC TLC taxi trip data was used as the source dataset.

The project uses a limited dataset sample for learning and portfolio purposes.

## 2. Bronze Layer

Raw data was loaded into:

`nyc_tlc.bronze.tlc_trips`

Record count:

`50,000`

The Bronze layer preserves the source data.

## 3. Silver Layer

The Bronze data was read using PySpark.

Data quality checks included:

- NULL values
- Duplicate records
- Invalid numeric values
- Timestamp validation

Data types were standardized.

Invalid financial records were removed.

Silver table:

`nyc_tlc.silver.cleaned_tlc_trips`

Record count:

`49,503`

## 4. Derived Columns

The following columns were created:

- trip_duration_minutes
- pickup_date
- pickup_hour

## 5. Gold Layer

Three business-level tables were created:

### Daily Taxi Performance

`nyc_tlc.gold.daily_taxi_performance`

### Payment Analysis

`nyc_tlc.gold.payment_analysis`

### Peak Hour Analysis

`nyc_tlc.gold.peak_hour_analysis`

## 6. Workflow

A Databricks Workflow was created to execute the ETL notebook.

The workflow was successfully tested and scheduled for daily execution.

## 7. Architecture

```text
Bronze
  |
  v
Silver
  |
  v
Gold
  |
  +--> Daily Taxi Performance
  +--> Payment Analysis
  +--> Peak Hour Analysis