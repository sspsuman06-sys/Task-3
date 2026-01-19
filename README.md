# DATA ANALYST INTERNSHIP – TASK 3

## SQL Basics: Filtering, Sorting & Aggregations

### Dataset Used

**Superstore Dataset (CSV)**

---

## Project Structure

```
Task_3_SQL_Basics/
│── dataset/
│   └── superstore.csv
│── queries_task3.sql
│── sales_summary.csv
│── README.md
```

---

## 1. Database & Table Creation

A new database and table were created in MySQL/PostgreSQL with appropriate data types.


CREATE DATABASE superstore_db;
USE superstore_db;

CREATE TABLE superstore_sales (
    order_id VARCHAR(50),
    order_date DATE,
    ship_date DATE,
    ship_mode VARCHAR(50),
    customer_id VARCHAR(50),
    customer_name VARCHAR(100),
    segment VARCHAR(50),
    country VARCHAR(50),
    city VARCHAR(50),
    state VARCHAR(50),
    region VARCHAR(50),
    category VARCHAR(50),
    sub_category VARCHAR(50),
    product_name VARCHAR(200),
    sales DECIMAL(10,2),
    quantity INT,
    discount DECIMAL(4,2),
    profit DECIMAL(10,2)
);


##2. Data Import

The CSV file was imported using MySQL Workbench / PgAdmin Import Wizard.

---

## 3. Basic Data Exploration


SELECT COUNT(*) FROM superstore_sales;
SELECT * FROM superstore_sales LIMIT 10;


## 4. Filtering & Sorting Queries


-- Technology category sales
SELECT * FROM superstore_sales
WHERE category = 'Technology';

-- Top 10 highest sales
SELECT product_name, sales FROM superstore_sales
ORDER BY sales DESC
LIMIT 10;



## 5. Aggregations & Group By

```sql
-- Total sales by category
SELECT category, SUM(sales) AS total_sales
FROM superstore_sales
GROUP BY category;

-- Average profit by region
SELECT region, AVG(profit) AS avg_profit
FROM superstore_sales
GROUP BY region;
```



## 6. HAVING Clause

```sql
SELECT category, SUM(sales) AS total_sales
FROM superstore_sales
GROUP BY category
HAVING SUM(sales) > 100000;
```

---

## 7. BETWEEN & LIKE Usage

```sql
-- Monthly sales report
SELECT * FROM superstore_sales
WHERE order_date BETWEEN '2017-01-01' AND '2017-01-31';

-- Customer name search
SELECT * FROM superstore_sales
WHERE customer_name LIKE '%Singh%';
```

---

## 8. Interview-Level Queries

```sql
-- Top 5 customers by total spend
SELECT customer_name, SUM(sales) AS total_spend
FROM superstore_sales
GROUP BY customer_name
ORDER BY total_spend DESC
LIMIT 5;
```

---

## 9. Export Result

Sales summary exported to sales_summary.csv
