# 🛍️ Customer Shopping Behavior Analysis

> End-to-end data analytics project using Python, PostgreSQL, and Power BI to uncover spending patterns, customer segments, and product trends from 3,900 retail transactions.

---

## 📌 Project Overview

Retailers often struggle to understand *why* customers buy, *who* their most valuable customers are, and *which* products drive revenue. This project tackles those questions head-on using a transactional dataset of 3,900 purchases across clothing, footwear, accessories, and outerwear categories.

The analysis spans the full analytics pipeline from raw data cleaning to SQL-driven business queries to an interactive Power BI dashboard and closes with actionable recommendations for marketing and retention strategy.

---

## 🗂️ Repository Structure
customer-shopping-behavior-analysis/

├── data/

│   └── shopping_behavior.csv          # Raw dataset (3,900 rows × 18 columns)

├── notebooks/

│   └── eda_cleaning.ipynb             # Python EDA and data preparation

├── sql/

│   ├── 01_revenue_by_gender.sql

│   ├── 02_high_spending_discount_users.sql

│   ├── 03_top5_products_by_rating.sql

│   ├── 04_shipping_type_comparison.sql

│   ├── 05_subscribers_vs_nonsubscribers.sql

│   ├── 06_discount_dependent_products.sql

│   ├── 07_customer_segmentation.sql

│   ├── 08_top3_products_per_category.sql

│   ├── 09_repeat_buyers_subscriptions.sql

│   └── 10_revenue_by_age_group.sql

├── dashboard/

│   └── customer_behavior_dashboard.pbix   # Power BI dashboard file

├── images/

│   └── dashboard_preview.png          # Dashboard screenshot

└── README.md

---

## 📊 Dataset Summary

| Attribute | Detail |
|---|---|
| Rows | 3,900 |
| Columns | 18 |
| Source | Synthetic retail transaction data |
| Missing Data | 37 null values in `review_rating` (imputed) |

**Feature categories:**
- **Demographics** — Age, Gender, Location, Subscription Status
- **Purchase details** — Item, Category, Amount (USD), Season, Size, Color
- **Behavior** — Discount Applied, Previous Purchases, Frequency, Review Rating, Shipping Type

---

## 🔧 Tools & Technologies

| Layer | Tool |
|---|---|
| Data Cleaning & EDA | Python (pandas, NumPy) |
| Database | PostgreSQL |
| SQL Analysis | pgAdmin / psycopg2 |
| Visualization | Power BI |

---

## 🐍 Python — EDA & Data Preparation

The notebook covers the full data preparation pipeline before SQL analysis:

- **Data Loading** — Imported dataset using `pandas`
- **Initial Exploration** — `df.info()` for structure, `.describe()` for summary statistics
- **Missing Data Handling** — Imputed 37 null `review_rating` values using the **median rating per product category**
- **Column Standardization** — Renamed all columns to `snake_case`
- **Feature Engineering**
  - `age_group` — Binned continuous age into generational segments (Young Adult, Adult, Middle-aged, Senior)
  - `purchase_frequency_days` — Derived numeric frequency from categorical frequency labels
- **Data Consistency Check** — Found `discount_applied` and `promo_code_used` were fully redundant; dropped `promo_code_used`
- **Database Integration** — Loaded cleaned DataFrame into PostgreSQL using `psycopg2`

---

## 🗄️ SQL Analysis — Business Questions

Ten business queries were written in PostgreSQL to answer real retail strategy questions:

| # | Query | Key Finding |
|---|---|---|
| 1 | Revenue by Gender | Male customers generated ~2× the revenue of female customers ($157,890 vs $75,191) |
| 2 | High-Spending Discount Users | 839 customers used discounts yet spent above average — a key retention target |
| 3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82) lead in customer satisfaction |
| 4 | Shipping Type Comparison | Express shipping correlates with slightly higher purchase amounts ($60.48 vs $58.46) |
| 5 | Subscribers vs. Non-Subscribers | Avg spend nearly identical — subscription value lies in volume, not per-order size |
| 6 | Discount-Dependent Products | Hat (50%), Sneakers (49.7%), Coat (49.1%) — highest discount dependency |
| 7 | Customer Segmentation | 3,116 Loyal / 701 Returning / 83 New customers |
| 8 | Top 3 Products per Category | Jewelry, Blouse, Sandals, and Jacket lead their respective categories |
| 9 | Repeat Buyers & Subscriptions | Repeat buyers (5+ purchases) are still majority non-subscribers — conversion opportunity |
| 10 | Revenue by Age Group | Young Adults lead revenue ($62,143), followed closely by Middle-aged ($59,197) |

---

## 📈 Power BI Dashboard

An interactive dashboard was built to allow business users to explore insights dynamically.

**Dashboard features:**
- KPI cards: Total Customers, Average Purchase Amount, Average Review Rating
- Subscription status breakdown (donut chart)
- Revenue and Sales by Category (bar charts)
- Revenue and Sales by Age Group (horizontal bar charts)
- **Filter panel:** Subscription Status, Gender, Category, Shipping Type

---

## 💡 Business Recommendations

| Recommendation | Rationale |
|---|---|
| **Boost subscription conversions** | Repeat buyers aren't subscribing — targeted nudges could increase the 27% subscription rate |
| **Loyalty rewards program** | 3,116 loyal customers are already retained; reward them to sustain and grow this segment |
| **Reassess discount strategy** | Products like Hat and Sneakers show ~50% discount rates — margins may be at risk |
| **Spotlight top-rated products** | Gloves, Sandals, and Boots rate highest — feature them prominently in marketing |
| **Target Young Adults** | Highest revenue-generating segment — prioritize in campaigns and product assortment |

---




