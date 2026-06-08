# 🛍️ Customer Shopping Behavior Analysis

> **End-to-end Data Analytics Portfolio Project** | Python · MS SQL Server · Power BI

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![SQL Server](https://img.shields.io/badge/MS%20SQL%20Server-T--SQL-red?logo=microsoftsqlserver)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Business Problem

A leading retail company wants to better understand its customers' shopping behavior to improve sales, customer satisfaction, and long-term loyalty. Management has noticed shifts in purchasing patterns across demographics, product categories, and sales channels.

> **Core Question:** *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

---

## 🗂️ Project Structure

```
customer-shopping-behavior-analysis/
│
├── Customer_Shopping_Behaviour.ipynb            # Phase 1: Python cleaning & EDA
├── SQLQuery2.sql                                # Phase 2: MS SQL Server queries (10 analyses)
├── Completed_Customer_Behaviour_Dashboard.pbix  # Phase 3: Power BI dashboard
├── customer_shopping_behavior.csv               # Raw dataset (3,900 records)
├── Customer_Shopping_Behavior_Analysis_Dev.pdf  # Full project report
├── Customer-Shopping-Behavior-Analysis.pptx     # Stakeholder presentation
└── README.md
```

---

## 🔧 Tech Stack

| Tool | Purpose |
|---|---|
| **Python (Pandas, SQLAlchemy)** | Data cleaning, feature engineering, DB connection |
| **MS SQL Server (T-SQL / SSMS)** | Structured business queries, customer segmentation |
| **Power BI** | Interactive dashboard & KPI visualization |
| **Jupyter Notebook** | EDA and documented Python workflow |

---

## 📊 Dataset

- **Rows:** 3,900 customer transactions  
- **Columns:** 18 features  
- **Key Fields:** `customer_id`, `age`, `gender`, `item_purchased`, `category`, `purchase_amount`, `review_rating`, `subscription_status`, `shipping_type`, `discount_applied`, `previous_purchases`, `frequency_of_purchases`  
- **Missing Data:** 37 nulls in `review_rating` → imputed using **category-level median**

---

## 🐍 Phase 1 — Python (Data Cleaning & Feature Engineering)

- Renamed all columns to **snake_case** format  
- Imputed missing `review_rating` using **groupby category median** (prevents cross-category bias)  
- Engineered `age_group` via `pd.qcut` → 4 equal-frequency bins: `young adult`, `adult`, `middle-aged`, `senior`  
- Engineered `purchase_frequency_days` by mapping text intervals (weekly → 7, monthly → 30, etc.)  
- Dropped redundant `promo_code_used` (identical boolean structure to `discount_applied`)  
- Loaded cleaned DataFrame into MS SQL Server via **SQLAlchemy**

---

## 🗄️ Phase 2 — MS SQL Server (Business Analysis)

All queries written in **T-SQL** and executed in **SQL Server Management Studio (SSMS)**.

| # | Business Question | Technique Used |
|---|---|---|
| Q1 | Revenue by Gender | `GROUP BY`, `SUM` |
| Q2 | High-spend discount users | Subquery, `AVG` |
| Q3 | Top 5 products by review rating | `TOP 5`, `ORDER BY` |
| Q4 | Standard vs Express shipping spend | `WHERE IN`, `ROUND`, `AVG` |
| Q5 | Subscriber vs non-subscriber spend | `COUNT`, `AVG`, `SUM` |
| Q6 | Most discount-dependent products | `CASE WHEN`, `CAST`, percentage calc |
| Q7 | Customer segmentation (New / Returning / Loyal) | **CTE** + `CASE WHEN` |
| Q8 | Top 3 products per category | **CTE** + `ROW_NUMBER() OVER (PARTITION BY)` |
| Q9 | Repeat buyers & subscription likelihood | `WHERE`, `GROUP BY` |
| Q10 | Revenue by age group | `GROUP BY`, `SUM`, `ORDER BY` |

---

## 📈 Phase 3 — Power BI Dashboard

Connected Power BI directly to **MS SQL Server** (local instance).

**DAX Measures:**
```dax
Total Customers = DISTINCTCOUNT(customer[customer_id])
Avg Purchase    = AVERAGE(customer[purchase_amount])
Avg Rating      = AVERAGE(customer[review_rating])
```

**Visuals built:**
- 🔢 KPI Cards — 3.9K customers · $59.76 avg purchase · 3.75 avg rating  
- 🍩 Donut Chart — Subscriber ratio (27% Yes / 73% No)  
- 📊 Clustered Column — Revenue & Sales by Category  
- 📊 Bar Charts — Revenue & Sales by Age Group  
- 🔘 Button Slicers — Category & Shipping Type filters

---

## 💡 Key Findings

| Insight | Finding |
|---|---|
| **Gender Revenue** | Male customers generated ~2x more revenue ($157,890 vs $75,191) |
| **Discount Anomaly** | 839 customers used discounts yet still spent above average |
| **Top Rated Products** | Gloves (3.86), Sandals (3.84), Boots (3.82) |
| **Shipping** | Express ($60.48) slightly outperforms Standard ($58.46) in avg spend |
| **Subscriptions** | Subscribers and non-subscribers spend nearly the same ($59.49 vs $59.87) |
| **Customer Loyalty** | 3,116 out of 3,900 customers classified as Loyal |
| **Top Age Group** | Young Adults lead revenue at $62,143 |

---

## ✅ Business Recommendations

1. **Boost Subscriptions** — Promote exclusive perks; subscriber spend potential equals non-subscribers  
2. **Loyalty Programs** — Reward repeat buyers to retain the 3,116 loyal customers  
3. **Review Discount Policy** — 839 high-spenders use discounts and don't need heavy discounting  
4. **Product Focus** — Prioritize Gloves, Sandals & Boots in campaigns (highest rated)  
5. **Targeted Marketing** — Focus on Young Adults & Express Shipping users (highest revenue segments)

---

## 🚀 How to Run

```bash
# 1. Clone the repo
git clone https://github.com/D3vra1/customer-shopping-behavior-analysis.git

# 2. Open Python notebook
jupyter notebook Customer_Shopping_Behaviour.ipynb

# 3. Run SQL queries in SSMS against your local SQL Server instance
# Open SQLQuery2.sql in SQL Server Management Studio (SSMS)

# 4. Open the Power BI dashboard
# Open Completed_Customer_Behaviour_Dashboard.pbix in Power BI Desktop
```

---

## 👤 Author

**Devraj Singh Sukhai**  
📍 Nanded, Maharashtra, India  
🎓 B.Tech Computer Science (2024)  
📜 Google Data Analytics Professional Certificate  
🔗 [GitHub](https://github.com/D3vra1)
Linkedin🔗 https://www.linkedin.com/in/devrajsingh-sukhai-670430249
---
*Built as a complete end-to-end portfolio project to demonstrate real-world Data Analyst skills.*
