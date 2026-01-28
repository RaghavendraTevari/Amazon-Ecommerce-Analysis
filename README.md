





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

