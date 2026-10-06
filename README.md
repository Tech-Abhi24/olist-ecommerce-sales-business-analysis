# Olist E-Commerce Sales & Business Analysis

An end-to-end **E-Commerce Data Analytics project** using PostgreSQL and Power BI to analyze sales performance, customer behavior, product categories, sellers, delivery performance, and customer reviews.

The project is based on the **Brazilian E-Commerce Public Dataset by Olist** and focuses on answering practical business questions that can help management identify growth opportunities, operational issues, and areas for improvement.

---

## 📌 Project Overview

E-commerce businesses generate large amounts of data across orders, customers, products, sellers, payments, reviews, and delivery operations.

This project analyzes Olist's e-commerce data to answer business-focused questions such as:

- How is revenue changing over time?
- Which product categories generate the most revenue?
- Which categories receive the most orders?
- Which states contribute the most revenue?
- Which sellers generate the highest revenue?
- How many customers are purchasing from the platform?
- What is the average order value?
- How much freight cost is associated with orders?
- How long does it take to deliver orders?
- Which states have longer delivery times?
- How does customer satisfaction relate to revenue?
- Which product categories have strong revenue but weaker customer ratings?
- How do repeat customers contribute to the business?
- Where are the major opportunities for business improvement?

The analysis was performed using **PostgreSQL for SQL-based analysis** and **Power BI for interactive business reporting and visualization**.

---

## 🎯 Business Objective

The main objective of this project is to transform raw e-commerce data into actionable business insights.

The analysis focuses on four major areas:

1. **Sales Performance**
2. **Customer & Product Behavior**
3. **Seller Performance**
4. **Operational & Customer Experience Analysis**

The final Power BI dashboard provides an executive-level view that can help stakeholders understand business performance and identify areas that require attention.

---

## 🛠️ Tools & Technologies

- **PostgreSQL** – Data querying and business analysis
- **pgAdmin 4** – Database management
- **Power BI** – Dashboard development and visualization
- **DAX** – Business measures and KPIs
- **Power Query** – Data preparation
- **GitHub** – Project documentation and version control

---

## 📂 Dataset

This project uses the **Brazilian E-Commerce Public Dataset by Olist**.

The dataset contains information related to:

- Customers
- Orders
- Order items
- Payments
- Reviews
- Products
- Sellers
- Product categories

The `geolocation` table was not included in the Power BI model because of its large size and limited relevance to the main business questions.

---

## 🗃️ Data Model

The project uses multiple related tables.

### Main Tables

| Table | Description |
|---|---|
| `customers` | Customer information and location |
| `orders` | Order information and timestamps |
| `order_items` | Products purchased in each order |
| `order_payments` | Payment information |
| `order_reviews` | Customer review scores |
| `products` | Product information and categories |
| `sellers` | Seller information and location |
| `product_category_translation` | Product category translations |

### Main Relationships

```text
customers
    │
    └── orders
          │
          ├── order_items ─── products
          │       │
          │       └── sellers
          │
          ├── order_payments
          │
          └── order_reviews
```



### 🔍 Data Analysis Process

The project followed an end-to-end analytics workflow:

```text

Raw Data
   ↓
PostgreSQL Database
   ↓
Data Cleaning & Validation
   ↓
SQL Business Analysis
   ↓
Power BI Data Model
   ↓
DAX Measures
   ↓
Interactive Dashboard
   ↓
Business Insights

```

### 📊 SQL Analysis

PostgreSQL was used to answer a series of business questions covering sales, customers, products, sellers, delivery, reviews, and operational performance.

The SQL analysis includes:

Sales & Revenue Analysis
Monthly revenue trends
Revenue by product category
Revenue by customer state
Average Order Value
Order volume analysis
Revenue and freight comparison
Product & Category Analysis
Top product categories by revenue
Top product categories by order volume
High-revenue categories
Low-rated high-revenue categories
Product category performance comparison
Customer Analysis
Total customers
One-time vs repeat customers
Repeat customer analysis
Customer growth over time
Monthly customer activity
Order growth over time
Seller Analysis
Top sellers by revenue
Seller performance comparison
Seller contribution to overall sales
Delivery & Customer Experience
Average delivery time
Delivery performance by state
Relationship between delivery time and customer reviews
Customer review score analysis
Business Opportunity Analysis

The final SQL analysis combines multiple business metrics to identify categories and areas with potential for improvement, including:

High revenue + high order volume
High revenue + low customer ratings
Strong customer satisfaction + lower revenue
High delivery time
High freight burden
📈 Power BI Dashboard

The final dashboard contains two pages designed for different business perspectives.

## Page 1 — E-Commerce Sales & Performance Overview

The first page provides an executive-level overview of overall business performance.

Key Performance Indicators
Total Revenue
Total Orders
Total Freight
Total Customers
Average Order Value
Average Review Score
Visualizations
Total Revenue by Year
Total Revenue by Product Category
Total Revenue by State

This page is designed to provide a quick understanding of the overall health and performance of the e-commerce business.

## Page 2 — Customer & Business Insights

The second page focuses on customer behavior, seller performance, delivery operations, and product-level insights.

Key Metrics
Average Delivery Days
Total Sellers
Visualizations
Orders by Product Category
Total Revenue by Seller
Revenue vs Customer Rating by Category
Average Delivery Days by State
Interactive Filters

The dashboard includes interactive slicers for:

Customer State
Year
Product Category

Slicers are synchronized across the dashboard so that selections can be used to analyze the business from different perspectives.

### 📌 Key DAX Measures

Some of the main Power BI measures used in the dashboard include:

## Total Revenue

```text

Total Revenue =
CALCULATE(
    SUM(order_items[price]),
    orders[order_status] = "delivered"
)
```

## Total Orders

```text
Total Orders =
CALCULATE(
    DISTINCTCOUNT(orders[order_id]),
    orders[order_status] = "delivered"
)
```

## Total Customers

```text
Total Customers =
DISTINCTCOUNT(orders[customer_id])
```

## Average Order Value

``` text
Average Order Value =
DIVIDE(
    [Total Revenue],
    [Total Orders]
)
```

## Total Freight

``` text
Total Freight =
CALCULATE(
    SUM(order_items[freight_value]),
    orders[order_status] = "delivered"
)
```

## Average Review Score

```text
Average Review Score =
AVERAGE(order_reviews[review_score])
```

## Average Delivery Days

```text
Average Delivery Days =
AVERAGEX(
    FILTER(
        orders,
        orders[order_status] = "delivered"
            && NOT ISBLANK(orders[order_delivered_customer_date])
            && NOT ISBLANK(orders[order_purchase_timestamp])
    ),
    DATEDIFF(
        orders[order_purchase_timestamp],
        orders[order_delivered_customer_date],
        DAY
    )
)
```


## Orders by Category
```text
Orders by Category =
DISTINCTCOUNT(order_items[order_id])
```

## Total Sellers
```text
Total Sellers =
DISTINCTCOUNT(order_items[seller_id])
```

## 💡 Business Insights

The dashboard is designed to help stakeholders answer important business questions such as:

1. Revenue Performance

Revenue trends can be monitored over time to identify periods of growth and changes in sales performance.

2. Product Category Performance

Comparing revenue and order volume helps identify categories that are driving sales and categories that may require additional attention.

3. Geographic Performance

State-level analysis highlights regions contributing strongly to revenue and helps identify geographic differences in business performance.

4. Seller Performance

Seller-level revenue analysis helps identify the highest-contributing sellers and understand seller concentration within the marketplace.

5. Customer Experience

Customer review scores provide an indication of customer satisfaction and can be compared against revenue and order volume.

6. Delivery Performance

Average delivery time by state helps identify regions where logistics performance may require improvement.

7. Business Opportunities

Combining revenue, order volume, customer ratings, and delivery metrics helps identify areas where the business can:

Improve customer experience
Reduce delivery delays
Improve product performance
Support high-performing sellers
Focus on high-potential categories
Investigate high-revenue categories with lower customer satisfaction

## 📷 Dashboard Preview
Executive Overview

Customer & Business Insights

## 📁 Project Structure

```text

olist-ecommerce-sales-business-analysis/
│
├── README.md
│
├── sql/
│   └── olist_ecommerce_analysis.sql
│
├── powerbi/
│   └── olist_ecommerce_dashboard.pbix
│
└── screenshots/
    ├── executive_overview.png
    └── business_insights.png
```

## 🚀 How to Use

1. PostgreSQL

Create a PostgreSQL database and import the Olist dataset tables.

Run the SQL file:

sql/olist_ecommerce_analysis.sql

The SQL file contains the business analysis queries used in this project.

2. Power BI

Open:

powerbi/olist_ecommerce_dashboard.pbix

If necessary, update the PostgreSQL connection settings according to your local environment.

The dashboard contains two pages:

E-Commerce Sales & Performance Overview
Customer & Business Insights


## 🧠 Skills Demonstrated

This project demonstrates practical skills in:

SQL & Database Analysis
PostgreSQL
Joins
Aggregations
GROUP BY
ORDER BY
DISTINCTCOUNT
Date-based analysis
Business KPI calculations
Customer segmentation
Performance analysis
Power BI
Data modeling
Relationships
Power Query
DAX
KPI cards
Bar charts
Line charts
Scatter plots
Slicers
Cross-filtering
Synchronized slicers
Interactive dashboards
Business Analytics
Revenue analysis
Customer analysis
Product analysis
Seller analysis
Geographic analysis
Operational analysis
Customer experience analysis
Business opportunity identification

## 📌 Important Analytical Consideration

An order can contain multiple product items. Therefore, when calculating category-level order volume, distinct order IDs are used instead of simply counting rows from the order_items table.

For example:

COUNT(DISTINCT oi.order_id)

This prevents a single order containing multiple products from being counted multiple times.


## 🎯 Project Outcome

This project demonstrates how raw e-commerce data can be transformed into a practical business intelligence solution using SQL and Power BI.

The final solution combines:

Data → SQL Analysis → Business KPIs → Interactive Dashboard → Business Insights

The project is designed from a business decision-making perspective, rather than focusing only on technical data exploration.

## 👤 Author

Abhishek Verma

MSc Data Science & Machine Learning
Carl von Ossietzky Universität Oldenburg, Germany

## Technical Skills

Python | SQL | PostgreSQL | Power BI | DAX | Excel | Power Query | Data Analysis | data Visualization

⭐ Project Focus

E-Commerce Analytics | Business Intelligence | SQL | PostgreSQL | Power BI | DAX


### बस ये structure रखना

```text
olist-ecommerce-sales-business-analysis/
│
├── README.md
├── sql/
│   └── olist_ecommerce_analysis.sql
├── powerbi/
│   └── olist_ecommerce_dashboard.pbix
└── screenshots/
    ├── executive_overview.png
    └── business_insights.png
```
