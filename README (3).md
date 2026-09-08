# Customer Shopping Behavior Analysis

End-to-end analysis of retail customer shopping behavior — from data cleaning to SQL-based business analysis to an interactive Power BI dashboard — aimed at helping a retail company identify trends, improve customer engagement, and optimize marketing and product strategy.

## Business Problem

A retail company wants to understand shifting purchasing patterns across demographics, product categories, and sales channels. The goal is to answer:

> How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?

## Dataset

- **Rows:** 3,900 transactions
- **Columns:** 18
- **Key fields:** customer demographics (age, gender, location, subscription status), purchase details (item, category, amount, season, size, color), shopping behavior (discount applied, promo code used, previous purchases, purchase frequency, review rating, shipping type)
- **Data quality:** 37 missing values in `Review Rating`, imputed using category-level median

## Project Workflow

### 1. Data Preparation & Cleaning (Python)
- Loaded data with `pandas`; explored structure with `df.info()` and `df.describe()`
- Imputed missing `Review Rating` values using the median rating per product category
- Standardized column names to snake_case
- Engineered new features: `age_group` (binned ages) and `purchase_frequency_days`
- Checked `discount_applied` vs `promo_code_used` for redundancy and dropped the latter
- Loaded the cleaned dataset into PostgreSQL for structured analysis

### 2. Data Analysis (SQL / PostgreSQL)
Queried the cleaned data to answer key business questions, including:
1. Revenue by gender
2. High-spending customers who still used discounts
3. Top 5 products by average review rating
4. Purchase amount comparison by shipping type
5. Subscribers vs. non-subscribers (spend and revenue)
6. Products most dependent on discounts
7. Customer segmentation (New / Returning / Loyal)
8. Top 3 products per category
9. Relationship between repeat purchases and subscription status
10. Revenue contribution by age group

### 3. Visualization (Power BI)
Built an interactive dashboard with filters for subscription status, gender, category, and shipping type, featuring:
- Key metrics: customer count, average purchase amount, average review rating
- Revenue and sales breakdown by category and age group
- Subscriber share (donut chart)

## Key Insights

- **Loyal customers** make up the largest segment (3,116 of 3,900), while new customers are a small share (83)
- Male customers generated significantly more revenue (~$157.9K) than female customers (~$75.2K)
- Non-subscribers generate far more total revenue (~$170K) than subscribers (~$62.6K), though average spend per customer is similar
- Discount-dependent products (Hat, Sneakers, Coat, Sweater, Pants) rely on discounts for nearly half of their purchases
- Young Adults contribute the highest revenue by age group, though the spread across groups is fairly even
- Express shipping customers spend slightly more on average than standard shipping customers

## Business Recommendations

- **Boost subscriptions** by promoting exclusive subscriber benefits
- **Launch loyalty programs** to convert returning customers into loyal ones
- **Review discount policy** to balance sales growth with margin control
- **Highlight top-rated, best-selling products** in marketing campaigns
- **Target high-revenue age groups and express-shipping users** in marketing efforts

## Tech Stack

| Stage | Tools |
|---|---|
| Data Cleaning & Feature Engineering | Python (pandas) |
| Structured Analysis | SQL (PostgreSQL) |
| Visualization | Power BI |

## Repository Structure

```
├── data/                  # Raw and cleaned dataset
├── notebooks/             # Python data cleaning & EDA scripts
├── sql/                   # SQL queries for business analysis
├── dashboard/             # Power BI dashboard file (.pbix)
├── report/                # Full project report
└── README.md
```

## How to Reproduce

1. Clone the repository
2. Install dependencies: `pip install pandas psycopg2`
3. Run the Python data cleaning script to generate the cleaned dataset
4. Load the cleaned dataset into PostgreSQL and run the SQL scripts in `sql/`
5. Open the `.pbix` file in Power BI to explore the dashboard
