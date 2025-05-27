

# 🛒 Retail Sales SQL Analysis (3000+ Transactions)

This beginner-friendly SQL project analyzes over **3000 rows of retail sales data** to uncover **business insights** about sales performance, customer behavior, and product trends.

## 📊 Project Overview

This project simulates real-world e-commerce analysis using SQL. You’ll find answers to questions like:

* Which month had the best sales?
* Who are the top 5 highest-paying customers?
* What time of day sees the most orders?
* How do male and female customers contribute to revenue?

> 📁 Dataset: Contains 3000+ retail sales records
> 🛠 Tools: MySQL
> 🎯 Focus: SQL querying, data cleaning, and business analysis

---

## ✅ Skills Demonstrated

* SQL querying with `SELECT`, `GROUP BY`, `ORDER BY`, `WHERE`, and `JOIN`
* Data cleaning and null checks
* Aggregation using `SUM()`, `AVG()`, `COUNT()`
* Temporal analysis using `MONTH()` and `YEAR()`
* Customer segmentation and behavioral insights

---

## 🗂 Table Schema

```sql
CREATE TABLE Retail_sales_table (
  transactions_id INT PRIMARY KEY,
  sale_date DATE,
  sale_time TIME,
  customer_id INT,
  gender VARCHAR(256),
  age INT,
  category VARCHAR(256),
  quantiy INT,
  price_per_unit FLOAT,
  cogs FLOAT,
  total_sale FLOAT
);
```

---

## 📌 Data Cleaning

```sql
SELECT * FROM Retail_sales_table
WHERE transactions_id IS NULL
  OR sale_date IS NULL
  OR sale_time IS NULL
  OR customer_id IS NULL 
  OR gender IS NULL
  OR age IS NULL
  OR category IS NULL
  OR quantiy IS NULL
  OR price_per_unit IS NULL
  OR cogs IS NULL
  OR total_sale IS NULL;
```

---

## 📈 Exploratory Data Analysis

### 1. Total Sales

```sql
SELECT COUNT(*) AS Total_sale FROM Retail_sales_table;
```

### 2. Unique Customers

```sql
SELECT COUNT(DISTINCT customer_id) FROM Retail_sales_table;
```

### 3. Distinct Categories

```sql
SELECT DISTINCT category FROM Retail_sales_table;
```

---

## 🔍 Business Insights with SQL

### Q1. Retrieve all sales made on `2022-11-05`

```sql
SELECT * FROM Retail_sales_table
WHERE sale_date = '2022-11-05';
```

---

### Q2. All Clothing transactions with quantity > 10 in November 2022

```sql
SELECT * FROM Retail_sales_table
WHERE category = 'clothing'
  AND quantiy > 10
  AND sale_date BETWEEN '2022-11-01' AND '2022-11-30';
```

---

### Q3. Total sales by category

```sql
SELECT category, SUM(total_sale) AS total_sales, COUNT(*) AS total_orders
FROM Retail_sales_table
GROUP BY category;
```

---

### Q4. Average age of customers in the Beauty category

```sql
SELECT ROUND(AVG(age), 2) AS Average_Age
FROM Retail_sales_table
WHERE category = 'Beauty';
```

---

### Q5. Transactions with total\_sale > 1000

```sql
SELECT * FROM Retail_sales_table
WHERE total_sale > 1000;
```

---

### Q6. Transactions by gender in each category

```sql
SELECT gender, category, COUNT(transactions_id) AS total_transactions
FROM Retail_sales_table
GROUP BY gender, category
ORDER BY category;
```

---

### Q7. Monthly average sale and best-selling month in each year

```sql
SELECT YEAR(sale_date) AS Year,
       MONTH(sale_date) AS Month,
       ROUND(AVG(total_sale), 2) AS Avg_sale
FROM Retail_sales_table
GROUP BY YEAR(sale_date), MONTH(sale_date)
ORDER BY Year, Month;
```

---

### Q8. Top 5 highest-paying customers

```sql
SELECT customer_id, SUM(total_sale) AS Total_sale
FROM Retail_sales_table
GROUP BY customer_id
ORDER BY Total_sale DESC
LIMIT 5;
```

---

### Q9. Unique customers per category

```sql
SELECT category, COUNT(DISTINCT customer_id) AS unique_customers
FROM Retail_sales_table
GROUP BY category
ORDER BY unique_customers DESC;
```

---

### Q10. Revenue by Gender

```sql
SELECT gender, SUM(total_sale) AS total_revenue
FROM Retail_sales_table
GROUP BY gender
ORDER BY total_revenue DESC;
```

---

## 💼 Project Purpose

This project helps demonstrate:

* My ability to work with **realistic datasets**
* Use of SQL to deliver **business insights**
* Understanding of **customer and sales analytics**
* Portfolio-worthy SQL project as an **aspiring Data Analyst**

---

## 📁 Files Included

* 'Retail_Sales_Analysis.sql' – All cleaned and final queries

* 'Retail_Sales_Dataset.csv' – Sample dataset (3,000+ rows)

---

## 📌 How to Use

1. Clone the repository
2. Import the SQL script into MySQL Workbench
3. Run each query step-by-step to explore the dataset
4. Modify queries or add your own!





