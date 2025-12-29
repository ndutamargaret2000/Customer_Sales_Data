# Customer_Sales_Data
📊 Sales Data Analysis using SQL, Python & Power BI
📌 Project Overview

This project analyzes sales data to understand how customer demographics, purchasing behavior, and subscription status affect sales performance. The analysis was conducted using PostgreSQL, Python, and Power BI, covering data cleaning, querying, and visualization.

🎯 Objectives

Analyze sales performance across customer demographics (age, gender, location)

Understand the impact of discounts, subscriptions, and shipping types on revenue

Identify high-performing products and categories

Segment customers based on purchase behavior

Build an interactive dashboard to communicate insights

🛠️ Tools & Technologies

SQL (PostgreSQL) – Data querying and analysis

Python (Pandas, SQLAlchemy, psycopg2) – Data cleaning, transformation, and loading

Power BI – Data visualization and dashboarding

VS Code – Development environment

📂 Dataset

Source: Kaggle (Shopping Trends Dataset)

Description: Transaction-level sales data containing customer demographics, product details, purchasing behavior, and promotional information.

Key Columns

Customer ID

Age, Gender, Location

Item Purchased, Category

Purchase Amount (USD)

Shipping Type, Payment Method

Discount Applied, Subscription Status

Review Rating

Previous Purchases

Frequency of Purchases

🧹 Data Preparation (Python)

Key steps performed using Python:

Loaded CSV data using Pandas

Standardized column names (lowercase, underscores)

Renamed purchase amount (usd) → purchase_amount

Created Age Groups using quartiles

Mapped purchase frequency to numerical days

Removed duplicate promotional column (promo_code_used)

Loaded cleaned data into PostgreSQL using SQLAlchemy

df.to_sql('sales', engine, if_exists='replace', index=False)

🧮 SQL Analysis (PostgreSQL)
Key Business Questions Answered

Total revenue by gender

Customers who used discounts but spent above average

Top 5 products by average review rating

Average purchase amount by shipping type

Spending comparison between subscribers and non-subscribers

Top 5 products with highest percentage of discounted purchases

Customer segmentation (New, Returning, Loyal)

Top 3 most purchased products within each category

Subscription likelihood among repeat buyers

Revenue contribution by age group

Example query:

SELECT 
    item_purchased,
    100 * SUM(CASE WHEN discount_applied = 'Yes' THEN 1 ELSE 0 END) / COUNT(*) 
        AS percent_of_purchases
FROM sales
GROUP BY item_purchased
ORDER BY percent_of_purchases DESC
LIMIT 5;

📊 Power BI Dashboard
## 📊 Power BI Dashboard

![Sales Dashboard](images/powerBI_dashboard.png)



An interactive Power BI dashboard was created to visualize:

Revenue by gender and age group

Product and category performance

Discount and subscription impact

Customer segments and purchase behavior

The dashboard enables stakeholders to quickly explore trends and insights.

🔍 Key Insights

Certain products rely heavily on discounts to drive purchases

Subscribed customers tend to have higher average spend and lifetime value

Loyal customers contribute a significant share of total revenue

Purchase behavior varies notably across age groups and shipping methods
