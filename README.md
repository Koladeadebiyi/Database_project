# 🎵 Chinook Database Analysis Project

## 📌 Project Overview
This project explores the Chinook SQLite database using Python, SQL, Pandas, and Matplotlib.  
The Chinook database represents a digital music store containing information about customers, invoices, tracks, artists, albums, and employees.

The objective of this project is to practice SQL querying directly from Python while performing business-oriented data analysis and visualization.

---

# 🚀 Technologies Used

- Python
- SQLite
- SQL
- Pandas
- Matplotlib
- Jupyter Notebook

---

# 📂 Database Used

The project uses the Chinook SQLite sample database.

Download link:

[Chinook SQLite Database](https://github.com/lerocha/chinook-database/blob/master/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite?utm_source=chatgpt.com)

https://roadmap.sh/projects/querying-sql-python
---

# 🎯 Project Objectives

The project answers the following business questions:

1. Which are the top 10 best-selling tracks?
2. Which country generates the highest revenue?
3. Who is the top-performing sales employee?
4. How can SQL query results be analyzed using Pandas?
5. How can business insights be visualized using charts?

---

# 🗂️ Database Schema Overview

Main tables used:

| Table | Description |
|---|---|
| Customer | Music store customers |
| Invoice | Customer purchases |
| InvoiceLine | Individual tracks purchased |
| Track | Song information |
| Album | Album details |
| Artist | Artist information |
| Employee | Sales support employees |

### Relationship Flow

```text
Employee → Customer → Invoice → InvoiceLine → Track → Album → Artist
```

---

# 🔌 Connecting to the Database

```python
import sqlite3
import pandas as pd

conn = sqlite3.connect("Chinook_Sqlite.sqlite")
```

---

# 📊 SQL Queries

## 1️⃣ Top 10 Best-Selling Tracks

```sql
SELECT 
    t.Name AS Track,
    SUM(il.Quantity) AS Total_Sold
FROM InvoiceLine il
JOIN Track t ON il.TrackId = t.TrackId
GROUP BY t.TrackId
ORDER BY Total_Sold DESC
LIMIT 10;
```

---

## 2️⃣ Country with Highest Revenue

```sql
SELECT 
    BillingCountry AS Country,
    SUM(Total) AS Revenue
FROM Invoice
GROUP BY BillingCountry
ORDER BY Revenue DESC;
```

---

## 3️⃣ Top Performing Employee

```sql
SELECT 
    e.FirstName || ' ' || e.LastName AS Employee,
    SUM(i.Total) AS Total_Sales
FROM Employee e
JOIN Customer c ON e.EmployeeId = c.SupportRepId
JOIN Invoice i ON c.CustomerId = i.CustomerId
GROUP BY e.EmployeeId
ORDER BY Total_Sales DESC;
```

---

# 📈 Visualization

Example bar chart visualization using Matplotlib:

```python
import matplotlib.pyplot as plt

top_tracks.plot(
    kind='bar',
    x='Track',
    y='Total_Sold',
    figsize=(10,5),
    legend=False
)

plt.title("Top 10 Best-Selling Tracks")
plt.ylabel("Units Sold")
plt.xticks(rotation=45)
plt.show()
```

---

#  Key Learnings

Through this project, I learned:

- How to connect Python to a SQLite database
- How to write SQL queries inside Jupyter Notebook
- How to use:
  - SELECT
  - JOIN
  - GROUP BY
  - ORDER BY
  - Aggregate functions
- How to load SQL query results into Pandas DataFrames
- How to visualize business insights using Matplotlib
- How relational databases work using primary and foreign keys

---

# 📌 Conclusion

This project demonstrates how SQL and Python can work together for data analysis.  
SQL was used to efficiently query structured relational data, while Python and Pandas were used for analysis and visualization.

The project also provided practical experience in querying relational databases and extracting business insights from transactional data.


