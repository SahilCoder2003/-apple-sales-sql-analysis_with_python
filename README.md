# -apple-sales-sql-analysis_with_python
End-to-end Apple sales analysis using SQL and Python – includes database design, queries, and visualizations.
# 🍎 Apple Sales SQL + Python Analysis

- 👨‍💻 Author: Sahil
- 📅 Project Type: SQL + Python (Data Analytics)
- 📊 Tools Used: PostgreSQL, SQLAlchemy, Pandas, Matplotlib, Seaborn

# 📝 Introduction

## This project analyzes Apple sales data using SQL and Python.
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
 
