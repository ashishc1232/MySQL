

##  What is a Subquery?

A **subquery** (also called an **inner query** or **nested query**) is a query that is placed inside another SQL query, usually inside:

* `SELECT`
* `FROM`
* `WHERE`
* `HAVING`
* `JOIN` (as a derived table)

---

## 🧠 Types of Subqueries

1. **Single-row Subquery** – returns one row.
2. **Multiple-row Subquery** – returns multiple rows.
3. **Multiple-column Subquery** – returns multiple columns.
4. **Correlated Subquery** – uses values from the outer query.
5. **Nested Subquery** – a subquery inside another subquery.

---

## 📘 Syntax

```sql
SELECT column1
FROM table1
WHERE column2 = (SELECT column2 FROM table2 WHERE condition);
```

---

## ✅ Example Database

Let's assume you have two tables:

### `employees`

| emp\_id | name    | dept\_id | salary |
| ------- | ------- | -------- | ------ |
| 1       | Alice   | 10       | 50000  |
| 2       | Bob     | 20       | 60000  |
| 3       | Charlie | 10       | 70000  |
| 4       | David   | 30       | 55000  |

### `departments`

| dept\_id | dept\_name |
| -------- | ---------- |
| 10       | HR         |
| 20       | IT         |
| 30       | Marketing  |

---

## 📌 Examples of Subqueries

### 1. **Subquery in `WHERE` (Single-row)**

👉 **Find employees working in the 'IT' department.**

```sql
SELECT name
FROM employees
WHERE dept_id = (
    SELECT dept_id
    FROM departments
    WHERE dept_name = 'IT'
);
```

🔍 The subquery finds the `dept_id` for "IT", and the outer query returns employees with that `dept_id`.

---

### 2. **Subquery in `WHERE` (Multiple-row)**

👉 **Find employees working in either 'HR' or 'Marketing'.**

```sql
SELECT name
FROM employees
WHERE dept_id IN (
    SELECT dept_id
    FROM departments
    WHERE dept_name IN ('HR', 'Marketing')
);
```

---

### 3. **Subquery in `SELECT` Clause**

👉 **Show each employee’s name and the average salary of all employees.**

```sql
SELECT name,
       salary,
       (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;
```

---

### 4. **Correlated Subquery**

👉 **Find employees who earn more than the average salary in their department.**

```sql
SELECT name, salary, dept_id
FROM employees e1
WHERE salary > (
    SELECT AVG(salary)
    FROM employees e2
    WHERE e1.dept_id = e2.dept_id
);
```

🔍 The subquery is correlated because it refers to `e1.dept_id` from the outer query.

---

### 5. **Subquery in `FROM` Clause (Derived Table)**

👉 **Find the maximum salary per department using a subquery.**

```sql
SELECT dept_id, MAX(salary) AS max_salary
FROM (
    SELECT dept_id, salary
    FROM employees
) AS dept_salaries
GROUP BY dept_id;
```

---

### 6. **Using `EXISTS` with Subquery**

👉 **Find departments that have at least one employee.**

```sql
SELECT dept_name
FROM departments d
WHERE EXISTS (
    SELECT 1
    FROM employees e
    WHERE e.dept_id = d.dept_id
);
```

---


Bilkul! Neeche main `employees` aur `departments` tables ke liye complete SQL queries de raha hoon, including:

1. `CREATE TABLE` statements
2. `INSERT` statements with sample data

---



### 📌 1. Create `departments` Table

```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL
);
```

### 📌 2. Insert Data into `departments`

```sql
INSERT INTO departments (dept_id, dept_name) VALUES
(10, 'HR'),
(20, 'IT'),
(30, 'Marketing');
```

---

### 📌 3. Create `employees` Table

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    dept_id INT,
    salary DECIMAL(10,2),
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

### 📌 4. Insert Data into `employees`

```sql
INSERT INTO employees (emp_id, name, dept_id, salary) VALUES
(1, 'Alice', 10, 50000.00),
(2, 'Bob', 20, 60000.00),
(3, 'Charlie', 10, 70000.00),
(4, 'David', 30, 55000.00),
(5, 'Eve', 20, 75000.00),
(6, 'Frank', 30, 52000.00);
```

---








