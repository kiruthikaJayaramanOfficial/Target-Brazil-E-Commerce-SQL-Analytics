# 🎯 Target Brazil E-Commerce — SQL Analytics Case Study

> **Role:** Data Analyst / Data Scientist (Case Study)  
> **Tool:** Google BigQuery (Standard SQL)  
> **Domain:** E-Commerce | Retail Analytics | Business Intelligence  
> **Author:** Kiruthika J

---

## 📄 Project Report

The full project report (with all SQL queries, result screenshots, insights, and recommendations) is available as a PDF in this repository:

📥 **[`Traget_SQL_kiruthika.pdf`](./Traget_SQL_kiruthika.pdf)**

> Open the PDF for a complete walkthrough of every analysis — including query logic, BigQuery result tables, and business interpretations.

---

## 📌 Problem Statement

As a Data Analyst at **Target**, the objective is to analyze a Brazilian e-commerce dataset (hosted on Google BigQuery) to extract actionable insights and provide strategic business recommendations across:

- Customer geography & order behavior
- Seasonal and temporal trends
- Delivery performance & logistics efficiency
- Payment patterns & economic impact

---

## 🗄️ Dataset Overview

The dataset spans **September 2016 – October 2018** and covers Target's e-commerce operations in Brazil across **6 relational tables**:

| Table | Description |
|---|---|
| `customers` | Customer demographics — ID, city, state, zip code |
| `orders` | Order lifecycle — purchase, estimated & actual delivery timestamps |
| `order_items` | Item-level detail — product ID, price, freight value |
| `payments` | Payment method, installments, and payment value |
| `products` | Product metadata |
| `sellers` | Seller location and ID |

**Scale:** 27 states · 4,119 cities · 772 days of order history

---

## 🔍 Analysis Structure

### 1. Exploratory Data Analysis
| Sub-question | Key Finding |
|---|---|
| Column data types (`customers` table) | `customer_id`, `customer_unique_id`, `customer_city`, `customer_state` → STRING; `customer_zip_code_prefix` → INT64 |
| Order time range | Sep 4, 2016 → Oct 17, 2018 (772 days) |
| Geographic reach | 27 states, 4,119 cities |

---

### 2. In-Depth Order Trend Exploration

**A) Year-over-Year Order Growth**

| Year | No. of Orders | YoY Growth |
|---|---|---|
| 2016 | 329 | — |
| 2017 | 45,101 | +13,607% |
| 2018 | 54,011 | +20% |

> 📈 **Insight:** 4.5× growth from 2016 pilot phase to Aug 2018. The 2016 data represents a soft-launch/beta period.

**B) Monthly Seasonality**

Peak months: **May (10.6%)**, **August (10.9%)**, **July (10.4%)**  
Low months: **September (4.3%)**, **October (5.0%)** — likely due to dataset truncation.

> 💡 **Recommendation:** Align inventory planning with Q2–Q3 high-velocity periods; exclude partial months from baseline forecasting.

**C) Order Placement by Time of Day**

| Time of Day | Hour Range | Orders | Share |
|---|---|---|---|
| Dawn | 0–6 hrs | 5,242 | 5.27% |
| Morning | 7–12 hrs | 27,733 | 27.89% |
| **Afternoon** | **13–18 hrs** | **38,135** | **38.35%** |
| Night | 19–23 hrs | 28,331 | 28.49% |

> 💡 **Recommendation:** Schedule push notifications/email campaigns before the afternoon surge. Limit system maintenance to the Dawn window.

---

### 3. Regional E-Commerce Evolution

**A) Month-on-Month Orders by State**

São Paulo (SP) consistently dominates — often tripling the next largest markets (RJ, MG). The late-2016 → early-2017 volume jump marks the shift from pilot to full-scale operations.

> 💡 **Recommendation:** Double down on SE region logistics; use targeted marketing (not CAPEX) to test viability in low-volume states before supply chain expansion.

**B) Customer Distribution by State**

| Rank | State | Customers |
|---|---|---|
| 1 | SP | 40,302 |
| 2 | RJ | 12,384 |
| 3 | MG | 11,259 |
| 4 | RS | 5,277 |
| 5 | PR | 4,882 |

---

### 4. Economic Impact — Pricing & Freight

**A) Revenue Growth (Jan–Aug 2017 vs Jan–Aug 2018)**

> 📊 **136.98% increase** in payment value — revenue more than doubled in one year.

> 💡 **Recommendation:** Shift focus from acquisition to operational scalability; stress-test supply chain to prevent CX degradation.

**B) Average Order Price by State** *(Top 5)*

| State | Total Orders | Total Price (R$) | Avg Price (R$) |
|---|---|---|---|
| PB | 532 | 115,268 | 191.48 |
| AL | 411 | 80,315 | 180.89 |
| AC | 81 | 15,983 | 173.73 |
| RO | 247 | 46,141 | 165.97 |
| PA | 970 | 178,948 | 165.69 |

> 💡 **Recommendation:** Test shipping subsidies in high-AOV Northern states to incentivize purchase frequency; focus upselling mechanics in high-volume SP.

**C) Freight Cost Disparity**

| Highest Freight States | Avg Freight (R$) | Lowest Freight States | Avg Freight (R$) |
|---|---|---|---|
| RR | 42.98 | SP | 15.15 |
| PB | 42.72 | PR | 20.53 |
| RO | 41.07 | MG | 20.63 |
| AC | 40.07 | RJ | 20.96 |
| PI | 39.15 | DF | 21.04 |

> Northern states face freight costs **~2.8× higher** than SP — a major barrier to market penetration.

---

### 5. Delivery Performance Analysis

**A) Delivery Time Variability**

Fulfillment times range from **2 days** (fast) to **46 days** (delayed). Negative `diff_estimated_delivery` values indicate the system deliberately over-estimates delivery dates to inflate "on-time" metrics.

> 💡 **Recommendation:** Recalibrate delivery prediction models — excessive time-padding (delivering 25 days early) creates a false perception of slowness that hurts checkout conversion.

**B & C) Top 5 States — Fastest vs Slowest Delivery**

| Rank | Slowest State | Avg Days | Fastest State | Avg Days |
|---|---|---|---|---|
| 1 | RR | 28.98 | SP | 8.30 |
| 2 | AP | 26.73 | PR | 11.53 |
| 3 | AM | 25.99 | MG | 11.54 |
| 4 | AL | 24.04 | DF | 12.51 |
| 5 | PA | 23.32 | SC | 14.48 |

> RR customers wait **3.5× longer** than SP customers — a critical logistics gap.

**D) States with Largest Early-Delivery Margins**

| State | Avg Days Ahead of Estimate |
|---|---|
| AC | 20 days |
| AM | 19 days |
| RO | 19 days |
| AP | 19 days |
| RR | 16 days |

> 💡 **Recommendation:** Narrow the estimated-vs-actual gap for Northern states to improve transparency while maintaining a small safety buffer.

---

### 6. Payment Behavior Analysis

**A) Payment Type Trends (Month-on-Month)**

Credit card dominates consistently across 2016–2018. UPI, debit card, and voucher show gradual adoption growth.

> 💡 **Recommendation:** Keep credit card as primary checkout path; run targeted cashback/discount campaigns to accelerate UPI and debit card adoption, reducing single-rail dependency.

**B) Orders by Payment Installments**

| Installments | No. of Orders |
|---|---|
| 1 (full upfront) | 48,236 |
| 2 | 12,360 |
| 3 | 10,422 |
| 4 | 7,066 |
| 5 | 5,221 |
| 10 | 5,305 |

> Most customers prefer paying upfront or in very few installments. EMI is a minority preference.

> 💡 **Recommendation:** Streamline checkout for one-shot and short-tenure payments; reserve EMI promotions for high-ticket, price-sensitive segments.

---

## 💡 Key Strategic Recommendations Summary

| Area | Recommendation |
|---|---|
| **Growth** | Replicate 2017 scaling strategies; exclude 2016 from YoY baselines (soft-launch bias) |
| **Marketing** | Target afternoon window (1–6 PM) for campaigns; heaviest support staffing 1 PM–11 PM |
| **Regional** | Optimize SE logistics for margin; use 3PL partnerships to unlock Northern market |
| **Logistics** | Implement dynamic SLAs at checkout; establish micro-fulfillment node in the North |
| **Freight** | Dynamic freight subsidy tiers to offset Northern cost burden without CAPEX |
| **Payments** | Credit card primary path + incentivize UPI/debit for payment rail diversification |
| **Delivery ETA** | Recalibrate prediction model — excessive padding suppresses checkout conversion |

---

## 🛠️ Tools & Technologies

| Tool | Usage |
|---|---|
| **Google BigQuery** | Primary SQL execution environment |
| **Standard SQL** | Window functions, CTEs, JOINs, timestamp arithmetic |
| **BigQuery INFORMATION_SCHEMA** | Schema introspection |

---

## 📂 Repository Structure

```
📦 Target-Brazil-E-Commerce-SQL-Analytics
 ┣ 📄 README.md                    ← This file
 ┗ 📄 Traget_SQL_kiruthika.pdf     ← Full project report with queries, results & screenshots
```

---

## 👩‍💻 Author

**Kiruthika J**  
MSc Data Science  

[![GitHub](https://img.shields.io/badge/GitHub-kiruthikaJayaramanOfficial-181717?style=flat&logo=github)](https://github.com/kiruthikaJayaramanOfficial/Target-Brazil-E-Commerce-SQL-Analytics)

---

*This project was completed as part of a data analytics case study assignment. All queries were executed on Google BigQuery against a real-world Brazilian e-commerce dataset.*
