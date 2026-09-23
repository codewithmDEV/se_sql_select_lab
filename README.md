# SQL Select Lab — Northwinds Employee & Order Data

A Python + SQLite lab exploring core SQL techniques: filtering, aliasing, CASE statements, string functions, numeric functions, and date formatting.

## 📌 Overview

This lab uses the Northwinds company database (`data.sqlite`) to practice querying relational data from Python using `sqlite3` and `pandas`. Queries are loaded into DataFrames and verified with `pytest`.

## 🛠️ Tech Stack

- **Python 3**
- **SQLite** — database engine
- **pandas** — data loading and manipulation
- **pytest** — automated testing

## 📁 Project Structure

```text
se_sql_select_lab/
│
├── main.py           # All SQL queries + DataFrame assignments
├── test_main.py      # Autotests for each step
├── data.sqlite       # Northwinds database
├── Pipfile           # Original dependencies (pandas, pytest)
├── Pipfile.lock
└── README.md
```

## 🚀 How to Run

### 1. Create a virtual environment

```bash
python3 -m venv .venv
```

### 2. Activate the virtual environment

Linux/macOS:

```bash
source .venv/bin/activate
```

Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install pandas pytest
```

### 4. Start the script

```bash
python3 main.py
```

### 5. Run the tests

```bash
pytest
```

## 🧠 What This Lab Covers

| Step | Skill | Query Feature |
| :--- | :--- | :--- |
| 1 | Connect to SQLite | `sqlite3.connect()` |
| 2 | Select specific columns | `SELECT col1, col2 FROM ...` |
| 3 | Column ordering | `SELECT col2, col1 FROM ...` |
| 4 | Aliasing | `SELECT col AS alias` |
| 5 | Conditional logic | `CASE WHEN ... THEN ... ELSE ... END` |
| 6 | String length | `LENGTH(col)` |
| 7 | Substrings | `SUBSTR(col, start, length)` |
| 8 | Numeric aggregation | `ROUND()`, `SUM()`, `.values` |
| 9 | Date formatting | `STRFTIME('%d', col)`, `'%m'`, `'%Y'` |

## 📊 Key Queries

### Select specific columns
```sql
SELECT employeeNumber, lastName FROM employees;
```

### Alias a column
```sql
SELECT lastName, employeeNumber AS ID FROM employees;
```

### CASE statement
```sql
SELECT jobTitle,
  CASE
    WHEN jobTitle = 'President' OR jobTitle = 'VP Sales' OR jobTitle = 'VP Marketing'
      THEN 'Executive'
    ELSE 'Not Executive'
  END AS role
FROM employees;
```

### String length
```sql
SELECT LENGTH(lastName) AS name_length FROM employees;
```

### Substring
```sql
SELECT SUBSTR(jobTitle, 1, 2) AS short_title FROM employees;
```

### Numeric sum
```sql
SELECT SUM(ROUND(priceEach * quantityOrdered)) AS total_price FROM orderDetails;
```

### Date extraction
```sql
SELECT orderDate,
  STRFTIME('%d', orderDate) AS day,
  STRFTIME('%m', orderDate) AS month,
  STRFTIME('%Y', orderDate) AS year
FROM orders;
```

## ✅ Test Results

```text
9 passed
```

All 9 autotests pass across:
- Connection
- Basic select filtering
- Aliasing
- CASE function
- String functions
- Numeric functions
- Date formatting

## 🧠 Lessons Learned

- **Database-specific syntax matters** — `EXTRACT()` works in PostgreSQL, but SQLite uses `STRFTIME()`
- **Table names are case-sensitive** in some contexts — `orderdetails` vs `orderDetails`
- **Aliases rename output, not the actual column**
- **`.values` strips pandas labels** so positional indexing works
- **`LENGTH()` and `SUBSTR()`** for string manipulation
- **`CASE` needs `ELSE`** to avoid `NULL` results
- **`pd.read_sql`** — one word, one underscore

## 👤 Author

**Mohamed Ahmed** — Full-Stack Engineer  
[Portfolio](https://codewithmdev.netlify.app) · [GitHub](https://github.com/codewithmDEV)