
# SQL Aggregations on Employee Table

## Introduction
The **Employee** table contains details of employees such as their department, salary, hire date, and city.  
Aggregation functions in SQL help us summarize this data and extract meaningful insights.  
This document explains **10 SQL aggregation queries** with examples using the Employee table.

---

##  Employee Table (Sample Data)

| emp_id | name    | department | salary | hire_date  | city      |
|--------|---------|------------|--------|------------|-----------|
| 1      | Alice   | HR         | 5000   | 2020-01-15 | Mumbai    |
| 2      | Bob     | IT         | 7000   | 2019-03-12 | Delhi     |
| 3      | Charlie | Finance    | 6000   | 2021-07-23 | Bangalore |
| 4      | David   | IT         | 8000   | 2018-11-05 | Chennai   |
| 5      | Emma    | HR         | 5500   | 2022-02-18 | Hyderabad |
| 6      | Frank   | Finance    | 6200   | 2017-09-14 | Pune      |
| 7      | Grace   | IT         | 9000   | 2020-12-01 | Mumbai    |
| 8      | Hannah  | Marketing  | 4500   | 2021-05-11 | Kolkata   |
| 9      | Ian     | Marketing  | 4700   | 2019-08-30 | Delhi     |
| 10     | Jack    | IT         | 7500   | 2023-01-10 | Hyderabad |

---

## 🔹 1. COUNT()
Count total number of employees.
```sql
SELECT COUNT(*) AS total_employees
FROM employee;
````

---

## 🔹 2. COUNT(DISTINCT)

Count how many unique departments exist.

```sql
SELECT COUNT(DISTINCT department) AS unique_departments
FROM employee;
```

---

## 🔹 3. SUM()

Find the total salary paid to all employees.

```sql
SELECT SUM(salary) AS total_salary
FROM employee;
```

---

## 🔹 4. AVG()

Find the average salary of employees.

```sql
SELECT AVG(salary) AS average_salary
FROM employee;
```

---

## 🔹 5. MIN()

Find the lowest salary in the company.

```sql
SELECT MIN(salary) AS min_salary
FROM employee;
```

---

## 🔹 6. MAX()

Find the highest salary in the company.

```sql
SELECT MAX(salary) AS max_salary
FROM employee;
```

---

## 🔹 7. GROUP BY + AVG()

Find the average salary in each department.

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employee
GROUP BY department;
```

---

## 🔹 8. GROUP BY + COUNT()

Count employees in each department.

```sql
SELECT department, COUNT(*) AS emp_count
FROM employee
GROUP BY department;
```

---

## 🔹 9. GROUP BY + SUM()

Find total salary per department.

```sql
SELECT department, SUM(salary) AS total_salary
FROM employee
GROUP BY department;
```

---

## 🔹 10. GROUP BY + MAX()

Find the highest salary in each department.

```sql
SELECT department, MAX(salary) AS highest_salary
FROM employee
GROUP BY department;
```

---

## Conclusion

* Aggregations like `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` help summarize data.
* Using them with `GROUP BY` allows analysis per department or city.
* These queries provide insights into salaries, employee distribution, and department-level statistics.


