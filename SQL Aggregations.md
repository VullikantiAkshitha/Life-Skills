
# SQL Aggregations – A Technical Overview

## Introduction
SQL aggregations allow us to perform calculations on a set of rows and return a single summarized value.  
They are commonly used with the `GROUP BY` clause to analyze data, create reports, and extract insights.  
This paper covers 10 commonly used SQL aggregation functions with explanations and examples.

---

## 1. COUNT()
- **Purpose:** Returns the number of rows that match a condition.
- **Syntax:**
  ```sql
  SELECT COUNT(*) FROM employees;
````

* **Example:** Count how many employees are in the company.

---

## 2. SUM()

* **Purpose:** Returns the total sum of a numeric column.
* **Syntax:**

  ```sql
  SELECT SUM(salary) FROM employees;
  ```
* **Example:** Calculate the total salary paid to employees.

---

## 3. AVG()

* **Purpose:** Returns the average value of a numeric column.
* **Syntax:**

  ```sql
  SELECT AVG(salary) FROM employees;
  ```
* **Example:** Find the average salary of employees.

---

## 4. MIN()

* **Purpose:** Returns the smallest value in a column.
* **Syntax:**

  ```sql
  SELECT MIN(salary) FROM employees;
  ```
* **Example:** Find the lowest salary in the company.

---

## 5. MAX()

* **Purpose:** Returns the largest value in a column.
* **Syntax:**

  ```sql
  SELECT MAX(salary) FROM employees;
  ```
* **Example:** Find the highest salary in the company.

---

## 6. GROUP\_CONCAT() (MySQL) / STRING\_AGG() (PostgreSQL)

* **Purpose:** Combines values from multiple rows into a single string.
* **Syntax (MySQL):**

  ```sql
  SELECT department, GROUP_CONCAT(name) 
  FROM employees 
  GROUP BY department;
  ```
* **Syntax (PostgreSQL):**

  ```sql
  SELECT department, STRING_AGG(name, ', ')
  FROM employees
  GROUP BY department;
  ```
* **Example:** List all employee names per department.

---

## 7. VARIANCE() / VAR\_SAMP()

* **Purpose:** Measures how spread out the values in a dataset are.
* **Syntax:**

  ```sql
  SELECT VAR_SAMP(salary) FROM employees;
  ```
* **Example:** Calculate the variance of salaries.

---

## 8. STDDEV() / STDDEV\_SAMP()

* **Purpose:** Returns the standard deviation of values.
* **Syntax:**

  ```sql
  SELECT STDDEV(salary) FROM employees;
  ```
* **Example:** Find how much salaries deviate from the average.

---

## 9. MEDIAN() (Some databases or via window functions)

* **Purpose:** Returns the middle value of a sorted dataset.
* **Syntax (PostgreSQL with percentile\_cont):**

  ```sql
  SELECT PERCENTILE_CONT(0.5) 
         WITHIN GROUP (ORDER BY salary) 
  FROM employees;
  ```
* **Example:** Find the median salary of employees.

---

## 10. COUNT(DISTINCT)

* **Purpose:** Counts unique (non-duplicate) values in a column.
* **Syntax:**

  ```sql
  SELECT COUNT(DISTINCT department) FROM employees;
  ```
* **Example:** Count how many unique departments exist.

---

## Aggregations with GROUP BY

Aggregation functions are most useful when combined with `GROUP BY`.
Example:

```sql
SELECT department, AVG(salary), COUNT(*) 
FROM employees
GROUP BY department;
```

This query shows the average salary and employee count for each department.

---

## Conclusion

Aggregation functions in SQL are powerful tools for data analysis.
They allow us to:

* Summarize large datasets
* Perform statistical analysis
* Generate business reports

By mastering these 10 aggregation functions, one can handle a wide variety of analytical queries efficiently.

