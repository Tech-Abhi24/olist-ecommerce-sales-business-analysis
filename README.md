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

Total Revenue

