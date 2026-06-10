# 🛒 Target Brazil E-Commerce SQL Analytics

<p align="center">
  <img src="https://img.shields.io/badge/SQL-BigQuery-blue?style=for-the-badge&logo=googlecloud&logoColor=white"/>
  <img src="https://img.shields.io/badge/Platform-Google%20BigQuery-orange?style=for-the-badge&logo=googlebigquery&logoColor=white"/>
  <img src="https://img.shields.io/badge/Domain-E--Commerce%20Analytics-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Region-Brazil-yellow?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge"/>
</p>

---

## 📌 Project Title

**Target Brazil E-Commerce SQL Analytics — Business Case Study**

---

## 📝 Project Description

### Short Description
A comprehensive SQL-based business case analysis of Target's e-commerce operations in Brazil, covering customer behaviour, order trends, regional distribution, payment patterns, freight logistics, and delivery performance — all queried from a multi-table BigQuery dataset.

### Detailed Description
This project performs an end-to-end exploratory and analytical deep-dive into Target's Brazilian e-commerce dataset using Google BigQuery SQL. The analysis spans six major analytical dimensions:

1. **Exploratory Data Analysis (EDA)** — Schema inspection, time range validation, geographic coverage
2. **In-depth Order Trend Analysis** — Year-over-year growth, quarterly seasonality, time-of-day ordering patterns
3. **Regional E-Commerce Evolution** — State-level order volumes and customer distribution across Brazil
4. **Economic Impact Analysis** — Payment values, order cost trends, and freight expenditure by region
5. **Delivery Performance Analysis** — Actual vs. estimated delivery times, top- and bottom-performing states
6. **Payment Behaviour Analysis** — Payment type trends, installment preferences, and UPI/credit card adoption

The dataset covers orders placed between **September 2016 and October 2018**, spanning **4,119 cities** across **27 Brazilian states**, with a total of **99,441 orders** analysed.

---

## 🎯 Objectives

- Understand the structural characteristics of Target's Brazil e-commerce dataset
- Identify temporal trends in order volume (yearly, quarterly, and daily)
- Analyse regional customer distribution and geographic concentration
- Quantify the economic impact through payment values and freight costs
- Evaluate delivery performance against estimated timelines
- Uncover payment method preferences and installment behaviour
- Provide actionable business recommendations at each analytical stage

---

## ✨ Key Features

- ✅ **Multi-table SQL joins** across `customers`, `orders`, `payments`, `order_items` tables
- ✅ **Window functions** (`LAG`, `ROW_NUMBER`) for year-over-year and ranking analysis
- ✅ **CTEs (Common Table Expressions)** for modular, readable query design
- ✅ **Date/time extraction** using `EXTRACT`, `DATE_DIFF` for temporal analysis
- ✅ **CASE-WHEN logic** for time-of-day segmentation (Dawn / Morning / Afternoon / Night)
- ✅ **Aggregation & grouping** for state-level, payment-type, and installment-level breakdowns
- ✅ **Structured insights framework** — every analysis includes Query → Result → Insights → Recommendations → Assumptions
- ✅ Covers **6 analytical sections** with **13 sub-questions** answered end-to-end

---

## ⚙️ Technologies, Frameworks & Libraries Used

| Category | Tool/Technology |
|---|---|
| **Query Language** | SQL (Standard SQL) |
| **Cloud Data Warehouse** | Google BigQuery |
| **Dataset Schema** | `scaler-dsml-sql-465413.target` |
| **Functions Used** | `EXTRACT`, `DATE_DIFF`, `LAG`, `ROW_NUMBER`, `CASE-WHEN`, `COUNT`, `SUM`, `AVG`, `ROUND` |
| **Clauses & Features** | CTEs (`WITH`), Window Functions (`OVER`), Subqueries, `INFORMATION_SCHEMA` |
| **Joins** | `JOIN`, `USING`, `ON` across multiple tables |
| **Platform** | Google Cloud Console / BigQuery UI |

---

## 📂 Project Structure

```
Target-Brazil-E-Commerce-SQL-Analytics/
│
├── README.md                          # Project documentation (this file)
│
├── 1_EDA/
│   ├── 1A_customer_column_datatypes.sql
│   ├── 1B_order_time_range.sql
│   └── 1C_city_state_count.sql
│
├── 2_InDepth_Exploration/
│   ├── 2A_yearly_order_trend.sql
│   ├── 2B_quarterly_seasonality.sql
│   └── 2C_time_of_day_orders.sql
│
├── 3_Regional_Evolution/
│   ├── 3A_monthly_orders_by_state.sql
│   └── 3B_customer_distribution_by_state.sql
│
├── 4_Economic_Impact/
│   ├── 4A_payment_value_yoy_growth.sql
│   ├── 4B_order_price_by_state.sql
│   └── 4C_freight_value_by_state.sql
│
├── 5_Delivery_Analysis/
│   ├── 5A_delivery_time_per_order.sql
│   ├── 5B_top_bottom_freight_states.sql
│   ├── 5C_top_bottom_delivery_time_states.sql
│   └── 5D_fastest_delivery_vs_estimate.sql
│
└── 6_Payment_Analysis/
    ├── 6A_monthly_orders_by_payment_type.sql
    └── 6B_orders_by_installment.sql
```

> 📝 *Note: Directory structure inferred from the analytical sections in the project report. Actual file names may vary.*

---

## 🔄 Workflow / Methodology

```
Dataset Import (BigQuery)
        │
        ▼
1. Exploratory Data Analysis
   └─ Schema inspection → Time range → Geographic coverage
        │
        ▼
2. In-Depth Order Trend Analysis
   └─ YoY growth → Quarterly seasonality → Time-of-day patterns
        │
        ▼
3. Regional E-Commerce Evolution
   └─ State-level monthly orders → Customer distribution
        │
        ▼
4. Economic Impact Analysis
   └─ YoY payment growth → Avg order value by state → Freight by state
        │
        ▼
5. Delivery Performance Analysis
   └─ Time-to-deliver → Freight rankings → Delivery time rankings → Early deliveries
        │
        ▼
6. Payment Behaviour Analysis
   └─ Payment type trends → Installment preferences
        │
        ▼
Insights + Recommendations (per section)
```

Each analysis section follows a consistent structure:
> **Query → Result Table → Insights → Recommendations → Assumptions**

---

## 📊 Results & Key Findings

### 1️⃣ Exploratory Analysis
| Metric | Value |
|---|---|
| Dataset Time Range | Sep 2016 – Oct 2018 |
| Total Unique Cities | 4,119 |
| Total States | 27 |
| Customer Table Columns | 5 (STRING & INT64 types) |

### 2️⃣ Order Trends
| Year | Orders | YoY Growth |
|---|---|---|
| 2016 | 329 | — |
| 2017 | 45,101 | ~13,608% |
| 2018 | 54,011 | ~19.7% |

- **Q1 2018** recorded the highest single-quarter volume at **21,208 orders**
- **Q4 2018** showed a dramatic anomalous drop to just **4 orders** — flagged for investigation
- **Afternoon** dominates order timing with **38,135 orders** (~38.5% of total)

### 3️⃣ Regional Distribution
- **São Paulo (SP)** accounts for **~44% of all customers** (40,302 unique customers)
- Top 5 states (SP, RJ, MG, RS, PR) represent **~72% of all customers**
- Northern/Northeastern states (RR, AP, AC, AM, TO) each hold **<1% share** — untapped market potential

### 4️⃣ Economic Impact
| Period | Total Payment Value | Growth |
|---|---|---|
| Jan–Aug 2017 | ₹3,669,022 | — |
| Jan–Aug 2018 | ₹8,694,734 | **+136.98%** |

- **PB** (Paraíba) has the highest average order value at **₹248.33**
- **SP** has the lowest average at **₹137.50** but the highest total (**₹5.99M**)

### 5️⃣ Freight & Delivery
| Metric | Best Performer | Worst Performer |
|---|---|---|
| Avg Freight (Lowest) | SP — ₹15.15 | RR — ₹42.98 |
| Avg Delivery (Fastest) | SP — 8.3 days | RR — 28.98 days |
| Earliest vs Estimate | AC — 20 days early | — |

- Freight costs in top states are **nearly 2× higher** than bottom states
- Top 5 fast-delivery states arrive **16–20 days ahead** of estimated dates

### 6️⃣ Payment Behaviour
- **Credit card** is the dominant payment method across all months
- **UPI** grew from 63 orders (Oct 2016) to 1,509 orders (Nov 2017) — rapid adoption
- **48,236 orders** (nearly half) are paid in a **single installment**
- Very few customers opt for **12+ installments**

---

## 🖼️ Output Screenshots

> *All result screenshots below are sourced directly from the project report.*

### Customer Table Schema
| column_name | data_type |
|---|---|
| customer_id | STRING |
| customer_unique_id | STRING |
| customer_zip_code_prefix | INT64 |
| customer_city | STRING |
| customer_state | STRING |

### Yearly Order Growth
| Year | Orders | Prev Year Orders |
|---|---|---|
| 2016 | 329 | null |
| 2017 | 45,101 | 329 |
| 2018 | 54,011 | 45,101 |

### Time-of-Day Order Distribution
| Time Interval | Orders |
|---|---|
| Afternoon (13–18h) | 38,135 |
| Night (19–23h) | 28,331 |
| Morning (7–12h) | 27,733 |
| Dawn (0–6h) | 5,242 |

### Top 5 States — Freight vs Delivery Time
| Rank | Highest Freight State | Avg Freight | Fastest Delivery State | Avg Days |
|---|---|---|---|---|
| 1 | RR | ₹42.98 | SP | 8.30 |
| 2 | PB | ₹42.72 | PR | 11.53 |
| 3 | RO | ₹41.07 | MG | 11.54 |
| 4 | AC | ₹40.07 | DF | 12.51 |
| 5 | PI | ₹39.15 | SC | 14.48 |

---

## 🚀 Applications & Use Cases

- **Retail & E-Commerce Analytics** — Regional performance benchmarking
- **Logistics Optimisation** — Identifying high-freight and high-delay zones for warehouse placement
- **Marketing Strategy** — Time-of-day and state-specific campaign planning
- **Financial Planning** — Tracking revenue growth and payment method adoption
- **Customer Segmentation** — Geographic and behavioral clustering for targeted offers
- **Business Intelligence Dashboards** — Feeding SQL results into BI tools like Looker or Tableau

---

## 🔮 Future Enhancements

- [ ] Build a **Looker Studio / Tableau dashboard** to visualise all query results interactively
- [ ] Add **customer cohort analysis** to track retention across months
- [ ] Integrate **product category analysis** for category-level revenue breakdown
- [ ] Perform **seller-level analysis** to identify top-performing vendors
- [ ] Incorporate **review/rating data** to correlate delivery time with customer satisfaction scores
- [ ] Build a **predictive model** for delivery time estimation using historical patterns
- [ ] Automate the pipeline with **BigQuery scheduled queries** for live reporting
- [ ] Investigate the **Q4 2018 anomaly** with operational logs for root cause analysis

---

## 📖 Installation & Usage Instructions

### Prerequisites
- A **Google Cloud** account with BigQuery access
- The Target Brazil dataset loaded under the schema: `scaler-dsml-sql-465413.target`

### Steps to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/kiruthikaJayaramanOfficial/Target-Brazil-E-Commerce-SQL-Analytics.git
   cd Target-Brazil-E-Commerce-SQL-Analytics
   ```

2. **Open Google BigQuery Console**
   - Navigate to [console.cloud.google.com/bigquery](https://console.cloud.google.com/bigquery)

3. **Load the dataset**
   - Import the Target Brazil tables (`customers`, `orders`, `payments`, `order_items`) into your BigQuery project under a dataset named `target`

4. **Run the SQL queries**
   - Open any `.sql` file from the relevant folder
   - Update the project/dataset prefix if needed (replace `scaler-dsml-sql-465413.target` with your project ID)
   - Execute in the BigQuery query editor

5. **Review results**
   - Each query produces a result table matching the screenshots documented in this README

---

## 🏷️ GitHub Topics / Keywords

```
sql bigquery e-commerce analytics brazil target retail
data-analysis business-intelligence order-analytics
customer-segmentation freight-analysis delivery-performance
payment-analytics exploratory-data-analysis sql-analytics
google-bigquery window-functions cte ecommerce-data
regional-analysis time-series-analysis kpi-analysis
data-science business-case sql-project portfolio-project
```

---

## 📌 Repository Labels / Categories

| Label | Color | Description |
|---|---|---|
| `SQL` | `#0075ca` | SQL queries and analysis |
| `BigQuery` | `#e4e669` | Google BigQuery specific |
| `EDA` | `#d73a4a` | Exploratory data analysis |
| `E-Commerce` | `#0e8a16` | Retail/e-commerce domain |
| `Business Analytics` | `#f9d0c4` | Business case study |
| `Portfolio Project` | `#c5def5` | Showcase project |
| `Data Analysis` | `#bfd4f2` | General data analysis |

---

## 💼 Resume-Ready Project Summary

> **Target Brazil E-Commerce SQL Analytics** | Google BigQuery | SQL
>
> Conducted an end-to-end business case analysis on Target's Brazilian e-commerce dataset (99K+ orders, 2016–2018) using Google BigQuery SQL. Designed and executed 13+ analytical queries across 6 business dimensions — including YoY order growth analysis (13,608% spike in 2017), regional customer distribution (SP contributing 44% of orders), freight and delivery benchmarking across 27 states, and payment behavior segmentation. Applied advanced SQL techniques including CTEs, window functions (LAG, ROW_NUMBER), multi-table JOINs, and date functions. Delivered structured insights and actionable business recommendations at each analytical stage.

---

## 🙏 Acknowledgements / References

- **Dataset**: Target Brazil E-Commerce dataset (provided via Scaler DSML program)
- **Platform**: [Google BigQuery](https://cloud.google.com/bigquery) — cloud data warehouse used for all analysis
- **Course Context**: Scaler DSML SQL Business Case Assignment
- **Inspiration**: Real-world e-commerce analytics frameworks used by major retail platforms

---

## 📜 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2024 Kiruthika Jayaraman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/kiruthikaJayaramanOfficial">Kiruthika Jayaraman</a>
</p>
