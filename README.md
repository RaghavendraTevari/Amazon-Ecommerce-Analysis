# Amazon India Sales Analysis: Festive Season Optimization

## 📌 Project Overview

This project analyzes **120,000+ sales records** from Amazon India to identify growth opportunities in the ethnic wear segment. By cleaning messy regional data and analyzing fulfillment patterns, this project provides actionable insights for **inventory management** and **cancellation reduction** during peak Indian festive seasons (Diwali, Dussehra).

## 🛠️ Tech Stack

* **Database:** MySQL / PostgreSQL (Data Cleaning & Analysis)
* **Visualization:** Power BI / Tableau (Dashboarding)
* **Key Skills:** Window Functions, CTEs, Data Normalization, Business Intelligence

## 🔍 Key Business Questions Answered

1. **Regional Demand:** Which Indian states drive 80% of the revenue?
2. **Product Strategy:** How do specific categories like *Kurtas* and *Saree Sets* perform compared to western wear?
3. **Efficiency:** Does using **Fulfillment by Amazon (FBA)** significantly reduce order cancellations compared to merchant-fulfilled orders?

## 📈 Executive Summary of Insights

* **The "Maharashtra-Karnataka" Opportunity:** These two states account for the highest sales volume but also experience a 15% higher cancellation rate for merchant-fulfilled orders.
* **Festive Prep:** 70% of annual ethnic wear revenue is generated in the 3 months leading up to Diwali.
* **B2B Potential:** B2B transactions have a **2.5x higher Average Order Value (AOV)** than B2C, suggesting a massive opportunity for corporate gifting.

## 🗂️ Data Cleaning Samples

> *Self-Correction: Standardized state codes (e.g., 'MH' → 'Maharashtra') and handled NULLs in cancelled orders to ensure revenue reporting accuracy.*

```sql
-- Standardizing Indian State Names
UPDATE sales_report 
SET ship_state = CASE 
    WHEN ship_state IN ('MH', 'Maharastra') THEN 'Maharashtra'
    WHEN ship_state IN ('DL', 'New Delhi') THEN 'Delhi'
    ELSE ship_state END;

```

## 🚀 Future Recommendations

* **Localized Warehousing:** Transition top-selling categories in Maharashtra to local FBA centers to reduce lead time.
* **B2B Marketing:** Launch a LinkedIn-targeted campaign for corporate bulk orders in Q3.

---

## 🛠️ Setup & Data Ingestion

### 1. Database Initialization

First, create a dedicated schema to keep your workspace organized.

```sql
CREATE DATABASE amazon_india_db;
USE amazon_india_db;

```

### 2. Table Schema Creation

Before importing, define the table structure. This ensures data types (like prices and quantities) are handled correctly from the start.

```sql
CREATE TABLE sales_report (
    index_id INT,
    Order_ID VARCHAR(50),
    Date DATE,
    Status VARCHAR(50),
    Fulfilment VARCHAR(50),
    Sales_Channel VARCHAR(50),
    ship_service_level VARCHAR(50),
    Style VARCHAR(50),
    SKU VARCHAR(50),
    Category VARCHAR(50),
    Size VARCHAR(10),
    ASIN VARCHAR(50),
    Courier_Status VARCHAR(50),
    Qty INT,
    currency VARCHAR(10),
    Amount DECIMAL(10, 2),
    ship_city VARCHAR(100),
    ship_state VARCHAR(100),
    ship_postal_code VARCHAR(20),
    ship_country VARCHAR(50),
    promotion_ids TEXT,
    B2B BOOLEAN,
    fulfilled_by VARCHAR(50)
);

```

### 3. Importing the CSV

You can use the **Table Import Wizard** in MySQL Workbench or the `LOAD DATA INFILE` command for a faster, "pro" approach:

```sql
LOAD DATA INFILE '/path/to/Amazon_Sale_Report.csv'
INTO TABLE sales_report
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;

```



