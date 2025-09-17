
## 1. What is a Subquery?

A **subquery** is a query nested inside another SQL query. It is used to perform operations where the result of one query depends on the result of another.

Subqueries are often used in:

* `SELECT` clause
* `FROM` clause
* `WHERE` clause

They are helpful in filtering, comparing, or computing data using the results of another query.

---

## 2. Types of Subqueries

1. **Single-row subquery** – Returns one row
2. **Multi-row subquery** – Returns multiple rows
3. **Multi-column subquery** – Returns multiple columns
4. **Scalar subquery** – Returns a single value (single row + single column)
5. **Correlated subquery** – Uses a value from the outer query
6. **Non-correlated subquery** – Independent of the outer query

---

## 3. Sample Tables and Data

### Table: `departments`

```sql
CREATE TABLE departments (
    department_id INT PRIMARY KEY,
    department_name VARCHAR(100)
);
```

### Table: `employees`

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT,
    salary DECIMAL(10,2)
);
```

### Insert Data

```sql
INSERT INTO departments VALUES
(1, 'HR'),
(2, 'IT'),
(3, 'Finance'),
(4, 'Marketing'),
(5, 'Operations');

INSERT INTO employees VALUES
(101, 'Amit', 1, 50000),
(102, 'Bhavna', 2, 65000),
(103, 'Chandan', 2, 72000),
(104, 'Deepa', 3, 55000),
(105, 'Eshan', 4, 47000),
(106, 'Farhan', 1, 52000),
(107, 'Gauri', 5, 60000),
(108, 'Harshit', 2, 68000),
(109, 'Isha', 3, 58000),
(110, 'Jatin', 5, 61000);
```

---

## 4. Subqueries in Different Clauses

### A. Subquery in WHERE Clause

**Find employees who earn more than the average salary:**

```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### B. Subquery in SELECT Clause

**Display employee names and their department names:**

```sql
SELECT name,
       (SELECT department_name 
        FROM departments 
        WHERE departments.department_id = employees.department_id) AS department
FROM employees;
```

### C. Subquery in FROM Clause (Inline View)

**Find average salary per department:**

```sql
SELECT department_id, avg_salary
FROM (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
) AS dept_avg;
```

### D. Subquery with IN

**Find employees who work in departments that exist in the departments table:**

```sql
SELECT * FROM employees
WHERE department_id IN (SELECT department_id FROM departments);
```

### E. Subquery with NOT IN

**Find employees who work in departments that are not in the departments table (assuming orphan data):**

```sql
SELECT * FROM employees
WHERE department_id NOT IN (SELECT department_id FROM departments);
```

### F. Subquery with ANY

**Find employees who earn more than any employee in department 1:**

```sql
SELECT * FROM employees
WHERE salary > ANY (SELECT salary FROM employees WHERE department_id = 1);
```

### G. Subquery with ALL

**Find employees who earn more than all employees in department 1:**

```sql
SELECT * FROM employees
WHERE salary > ALL (SELECT salary FROM employees WHERE department_id = 1);
```

### H. Subquery with EXISTS

**Find departments that have at least one employee:**

```sql
SELECT * FROM departments d
WHERE EXISTS (
    SELECT 1 FROM employees e WHERE e.department_id = d.department_id
);
```

### I. Subquery with NOT EXISTS

**Find departments that have no employees:**

```sql
SELECT * FROM departments d
WHERE NOT EXISTS (
    SELECT 1 FROM employees e WHERE e.department_id = d.department_id
);
```

### J. Correlated Subquery

**Find employees whose salary is greater than the average salary of their own department:**

```sql
SELECT * FROM employees e1
WHERE salary > (
    SELECT AVG(salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

---

## 5. Correlated vs Non-Correlated Subquery

| Feature     | Non-Correlated Subquery        | Correlated Subquery                        |
| ----------- | ------------------------------ | ------------------------------------------ |
| Dependency  | Independent of outer query     | Depends on outer query                     |
| Execution   | Executed once                  | Executed once per row of outer query       |
| Performance | Generally faster               | May be slower due to multiple executions   |
| Example     | AVG(salary) from all employees | AVG(salary) for each employee's department |

---

## 6. Common Interview Questions

### Q1. Difference between correlated and non-correlated subquery?

A correlated subquery depends on values from the outer query. A non-correlated subquery is executed independently of the outer query.

### Q2. How to find employees with the highest salary?

```sql
SELECT * FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
```

### Q3. How to find departments without employees?

```sql
SELECT * FROM departments d
WHERE NOT EXISTS (
    SELECT 1 FROM employees e WHERE e.department_id = d.department_id
);
```

### Q4. How to find duplicate employee names?

```sql
SELECT name, COUNT(*) AS cnt
FROM employees
GROUP BY name
HAVING COUNT(*) > 1;
```

---

## 7. Best Practices

* Always test subqueries independently first.
* Use aliases (`e1`, `d`, etc.) to improve readability.
* Replace correlated subqueries with `JOIN` when possible for performance.
* Scalar subqueries (returning one value) can be safely used in `SELECT` or `WHERE`.

---

## 8. Extra: Equivalent Query Using JOIN (For Better Performance)

**Same as above – find employee names and department names using JOIN instead of subquery:**

```sql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

This is often more efficient than using subqueries.

