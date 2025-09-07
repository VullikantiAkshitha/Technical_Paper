
# SQL Aggregations – Learning Guide

## Introduction
SQL aggregation functions are used to perform calculations on multiple rows of a table and return a single summarized result.  
They are widely used in reporting, analytics, and business intelligence.

This guide explains **10 important aggregation functions** with examples.

---

## 1. COUNT()
- **Description:** Returns the number of rows (or non-NULL values if a column is specified).
- **Query:**
  ```sql
  SELECT COUNT(*) AS total_employees
  FROM employees;
````

* **Result Example:**

  ```
  total_employees
  ----------------
  150
  ```

---

## 2. SUM()

* **Description:** Adds up the values in a numeric column.
* **Query:**

  ```sql
  SELECT SUM(salary) AS total_salary
  FROM employees;
  ```
* **Result Example:**

  ```
  total_salary
  -------------
  900000
  ```

---

## 3. AVG()

* **Description:** Finds the average of numeric values.
* **Query:**

  ```sql
  SELECT AVG(salary) AS avg_salary
  FROM employees;
  ```
* **Result Example:**

  ```
  avg_salary
  -----------
  6000
  ```

---

## 4. MIN()

* **Description:** Finds the smallest value in a column.
* **Query:**

  ```sql
  SELECT MIN(salary) AS lowest_salary
  FROM employees;
  ```
* **Result Example:**

  ```
  lowest_salary
  --------------
  2500
  ```

---

## 5. MAX()

* **Description:** Finds the largest value in a column.
* **Query:**

  ```sql
  SELECT MAX(salary) AS highest_salary
  FROM employees;
  ```
* **Result Example:**

  ```
  highest_salary
  ---------------
  15000
  ```

---

## 6. COUNT(DISTINCT)

* **Description:** Counts unique values.
* **Query:**

  ```sql
  SELECT COUNT(DISTINCT department) AS total_departments
  FROM employees;
  ```
* **Result Example:**

  ```
  total_departments
  -----------------
  5
  ```

---

## 7. GROUP\_CONCAT() / STRING\_AGG()

* **Description:** Combines multiple values into one string (DB-specific).
* **Query (PostgreSQL):**

  ```sql
  SELECT department, STRING_AGG(name, ', ') AS employees_list
  FROM employees
  GROUP BY department;
  ```
* **Result Example:**

  ```
  department   | employees_list
  -------------+-------------------------
  HR           | Alice, Bob, Charlie
  IT           | David, Emma
  ```

---

## 8. VARIANCE()

* **Description:** Measures the spread of values from the average.
* **Query:**

  ```sql
  SELECT VAR_SAMP(salary) AS salary_variance
  FROM employees;
  ```
* **Result Example:**

  ```
  salary_variance
  ----------------
  1200000
  ```

---

## 9. STDDEV()

* **Description:** Finds the standard deviation (how spread out values are).
* **Query:**

  ```sql
  SELECT STDDEV(salary) AS salary_stddev
  FROM employees;
  ```
* **Result Example:**

  ```
  salary_stddev
  --------------
  1095.44
  ```

---

## 10. MEDIAN() (via window functions)

* **Description:** Returns the middle value in ordered data.
* **Query (PostgreSQL):**

  ```sql
  SELECT PERCENTILE_CONT(0.5) 
         WITHIN GROUP (ORDER BY salary) AS median_salary
  FROM employees;
  ```
* **Result Example:**

  ```
  median_salary
  --------------
  5800
  ```

---

## Using GROUP BY

Aggregations become powerful when grouped.

```sql
SELECT department, AVG(salary) AS avg_salary, COUNT(*) AS emp_count
FROM employees
GROUP BY department;
```

**Sample Result:**

```
department | avg_salary | emp_count
-----------+------------+----------
HR         | 5500       | 10
IT         | 7000       | 20
```

---

## ✅ Conclusion

* Aggregations summarize large datasets into meaningful insights.
* Functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` are the most common.
* Advanced functions like `VARIANCE`, `STDDEV`, and `MEDIAN` are useful in statistics.
* Always pair with `GROUP BY` for grouped reporting.

