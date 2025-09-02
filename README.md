# -apple-sales-sql-analysis_with_python
End-to-end Apple sales analysis using SQL and Python – includes database design, queries, and visualizations.
# 🍎 Apple Sales SQL + Python Analysis

- 👨‍💻 Author: Sahil
- 📅 Project Type: SQL + Python (Data Analytics)
- 📊 Tools Used: PostgreSQL, SQLAlchemy, Pandas, Matplotlib, Seaborn

## 📝 Introduction

### This project analyzes Apple sales data using SQL and Python.
It demonstrates how to:

- Create and manage relational databases (PostgreSQL)

- Write analytical SQL queries

- Connect SQL with Python (SQLAlchemy + Pandas)

- Perform exploratory data analysis (EDA)

- Visualize results using Matplotlib & Seaborn

This is an end-to-end data analytics project suitable for portfolio building. 🚀

## 📂 Project Structure  

📦 apple-sales-sql-analysis  
 ┣ 📂 data  
 ┃ ┣ sales.csv  
 ┃ ┣ products.csv  
 ┃ ┣ stores.csv  
 ┃ ┣ warranty.csv  
 ┃ ┗ category.csv  
 ┣ 📂 sql  
 ┃ ┣ APPLE_SQL.sql           # Database schema + table creation  
 ┃ ┣ question_of_sql.sql     # All SQL queries  
 ┣ 📂 notebooks  
 ┃ ┗ sql_with_python.ipynb   # Jupyter Notebook with analysis  
 ┣ 📂 reports  
 ┃ ┗ Apple_Sales_SQL_Project.pdf  # Final project report (PDF)  
 ┣ 📜 README.md              # Project documentation  
 ┗ 📜 requirements.txt       # Python libraries needed  
 
## ⚡ Key SQL Queries
 ### 1️⃣ Monthly Sales Trend
```sql
SELECT DATE_TRUNC('month', sale_date) AS month, SUM(quantity*price) AS revenue
FROM sales
JOIN products ON sales.product_id = products.product_id
GROUP BY 1
ORDER BY 1;
```

### 2️⃣ Top 5 Products by Revenue
```sql
SELECT p.product_name, SUM(s.quantity * s.price) AS revenue
FROM sales s
JOIN products p ON s.product_id = p.product_id
GROUP BY p.product_name
ORDER BY revenue DESC
LIMIT 5;
 
```
 ### 3️⃣ Least Selling Product Each Month
 ```sql
WITH monthly_sales AS (
    SELECT DATE_TRUNC('month', sale_date) AS month, product_id, SUM(quantity) AS total_sales
    FROM sales
    GROUP BY 1,2
)
SELECT month, product_id, total_sales
FROM (
    SELECT month, product_id, total_sales,
           RANK() OVER(PARTITION BY month ORDER BY total_sales ASC) AS least_rank
    FROM monthly_sales
) t
WHERE least_rank = 1;
```
### 4️⃣ Customers Who Purchased in Jan 2025 but Not Feb 2025
```sql
SELECT DISTINCT s.customer_id
FROM sales s
WHERE TO_CHAR(s.sale_date, 'Mon-YYYY') = 'Jan-2025'
AND NOT EXISTS (
    SELECT 1 FROM sales x
    WHERE x.customer_id = s.customer_id
    AND TO_CHAR(x.sale_date, 'Mon-YYYY') = 'Feb-2025'
);

```
### 5️⃣ Average Warranty Claim Time
```sql
SELECT AVG(claim_date - sale_date) AS avg_claim_days
FROM warranty w
JOIN sales s ON s.sale_id = w.sale_id;

```
## 📊 Visualizations (Python)

- 📈 Monthly Sales Trend (Line Chart)

- 🔥 Top 5 Products by Revenue (Bar Chart)

- 📉 Least Selling Product Each Month (Grouped Bar Chart)

- 👥 Customer Retention & Churn (SQL + Pandas)

- 🛠️ Average Warranty Claim Time (Numeric Insight)

## ⚙️ Setup Instructions
```bash
git clone https://github.com/SahilCoder2003/apple-sales-sql-analysis.git
cd apple-sales-sql-analysis
```

## ✅ Conclusion

- iPhones and MacBooks are top-selling products.

- Accessories and minor products often have the least sales.

- Some customers churn after their first month of purchase.

- Average warranty claim time provides product quality insights.

This project proves how SQL and Python can be combined for real-world analytics and business insights.

## 🔗 Connect With Me

- 💼 www.linkedin.com/in/sahilf2003

- 📧 fsahil423@gmail.com
