# 🗄️ SQL Query Examples Guide

## Sample Data Tables

### 📋 employees table
| id | name | department | salary | hire_date | age | city |
|----|------|------------|--------|-----------|-----|------|
| 1 | Alice Johnson | Engineering | 85000 | 2020-03-15 | 28 | New York |
| 2 | Bob Smith | Marketing | 62000 | 2019-07-22 | 34 | Chicago |
| 3 | Carol Davis | Engineering | 92000 | 2018-11-08 | 31 | San Francisco |
| 4 | David Wilson | Sales | 58000 | 2021-01-12 | 26 | Boston |
| 5 | Emma Brown | HR | 55000 | 2020-09-03 | 29 | Seattle |
| 6 | Frank Miller | Engineering | 78000 | 2021-06-18 | 25 | Austin |
| 7 | Grace Lee | Marketing | 65000 | 2019-12-05 | 32 | Denver |
| 8 | Henry Taylor | Sales | 61000 | 2020-04-20 | 27 | Miami |

### 🛒 products table
| id | name | category | price | stock | rating |
|----|------|----------|-------|-------|--------|
| 1 | iPhone 14 | Electronics | 999 | 150 | 4.5 |
| 2 | MacBook Pro | Electronics | 2499 | 75 | 4.8 |
| 3 | Nike Air Max | Clothing | 120 | 300 | 4.2 |
| 4 | Coffee Maker | Home | 89 | 200 | 4.0 |
| 5 | Gaming Chair | Furniture | 299 | 50 | 4.3 |

---

## 1. 🎯 SELECT and FROM Examples

### Basic SELECT - Get all columns
```sql
SELECT * FROM employees;
```
**Purpose:** Retrieve all data from employees table

### Select specific columns
```sql
SELECT name, salary FROM employees;
```
**Purpose:** Show only employee names and salaries

### Select with calculated fields
```sql
SELECT name, salary, salary * 12 AS annual_salary FROM employees;
```
**Purpose:** Calculate annual salary and show it as a new column

### Select distinct values
```sql
SELECT DISTINCT department FROM employees;
```
**Purpose:** Get unique departments without duplicates

---

## 2. 🔍 WHERE Clause Examples

### Simple WHERE condition
```sql
SELECT * FROM employees WHERE department = 'Engineering';
```
**Purpose:** Find all engineering employees

### Numeric comparisons
```sql
SELECT name, salary FROM employees WHERE salary > 70000;
```
**Purpose:** Find employees earning more than $70,000

```sql
SELECT * FROM products WHERE price BETWEEN 100 AND 500;
```
**Purpose:** Find products in the $100-500 price range

### Text pattern matching
```sql
SELECT * FROM employees WHERE name LIKE 'A%';
```
**Purpose:** Find employees whose names start with 'A'

### Date comparisons
```sql
SELECT * FROM employees WHERE hire_date >= '2020-01-01';
```
**Purpose:** Find employees hired since 2020

---

## 3. 🔗 Logical Operators (AND, OR, NOT)

### AND operator
```sql
SELECT * FROM employees 
WHERE department = 'Engineering' AND salary > 80000;
```
**Purpose:** Find high-paid engineering employees

```sql
SELECT * FROM products 
WHERE category = 'Electronics' AND price < 1000 AND stock > 100;
```
**Purpose:** Find affordable electronics with good stock

### OR operator
```sql
SELECT * FROM employees 
WHERE department = 'Sales' OR department = 'Marketing';
```
**Purpose:** Find employees in sales or marketing

```sql
SELECT * FROM products 
WHERE category = 'Electronics' OR category = 'Home';
```
**Purpose:** Find products that are either electronics or home items

### NOT operator
```sql
SELECT * FROM employees WHERE NOT department = 'HR';
```
**Purpose:** Find all employees except HR staff

```sql
SELECT * FROM products WHERE NOT category = 'Clothing';
```
**Purpose:** Find all non-clothing products

### Complex combinations
```sql
SELECT * FROM employees 
WHERE (department = 'Engineering' OR department = 'Sales') 
  AND salary > 60000 
  AND age < 30;
```
**Purpose:** Find young, well-paid employees in technical or sales roles

---

## 4. 📊 Comparison Operators

### Equal to (=)
```sql
SELECT * FROM employees WHERE age = 28;
```

### Not equal to (!=, <>)
```sql
SELECT * FROM employees WHERE department != 'HR';
SELECT * FROM products WHERE price <> 999;
```

### Greater than (>)
```sql
SELECT * FROM products WHERE rating > 4.5;
```

### Less than (<)
```sql
SELECT * FROM employees WHERE age < 30;
```

### Greater than or equal to (>=)
```sql
SELECT * FROM employees WHERE salary >= 70000;
```

### Less than or equal to (<=)
```sql
SELECT * FROM products WHERE price <= 200;
```

### IN operator (multiple values)
```sql
SELECT * FROM employees WHERE department IN ('Engineering', 'Sales', 'Marketing');
```

### NULL checks
```sql
SELECT * FROM employees WHERE city IS NOT NULL;
SELECT * FROM employees WHERE city IS NULL;
```

---

## 5. 📈 ORDER BY (Sorting)

### Sort ascending (default)
```sql
SELECT * FROM employees ORDER BY salary;
```
**Purpose:** Show employees from lowest to highest salary

### Sort descending
```sql
SELECT * FROM employees ORDER BY salary DESC;
```
**Purpose:** Show employees from highest to lowest salary

### Multiple column sorting
```sql
SELECT * FROM employees ORDER BY department, salary DESC;
```
**Purpose:** Group by department, then sort by salary within each department

### Sort by calculated field
```sql
SELECT name, salary, salary * 12 AS annual_salary 
FROM employees 
ORDER BY annual_salary DESC;
```

### Sort with WHERE
```sql
SELECT * FROM employees 
WHERE department = 'Engineering' 
ORDER BY hire_date;
```
**Purpose:** Find engineering employees sorted by how long they've worked

---

## 6. 🎯 LIMIT (Limiting Results)

### Basic LIMIT
```sql
SELECT * FROM employees LIMIT 5;
```
**Purpose:** Show only the first 5 employees

### Top N results
```sql
SELECT * FROM employees ORDER BY salary DESC LIMIT 3;
```
**Purpose:** Find the 3 highest-paid employees

### LIMIT with OFFSET (skip first N rows)
```sql
SELECT * FROM employees ORDER BY salary DESC LIMIT 3 OFFSET 2;
```
**Purpose:** Skip top 2 earners, show next 3 highest-paid

### Pagination example
```sql
-- Page 1 (first 5 records)
SELECT * FROM products ORDER BY name LIMIT 5 OFFSET 0;

-- Page 2 (next 5 records)
SELECT * FROM products ORDER BY name LIMIT 5 OFFSET 5;
```

---

## 7. 🚀 Real-World Combined Examples

### E-commerce: Find bestselling affordable products
```sql
SELECT name, price, rating, stock 
FROM products 
WHERE price < 300 AND rating >= 4.0 AND stock > 0
ORDER BY rating DESC, stock DESC 
LIMIT 5;
```

### HR: Find junior developers for promotion
```sql
SELECT name, salary, age, hire_date
FROM employees 
WHERE department = 'Engineering' 
  AND age < 30 
  AND salary < 85000
  AND hire_date < '2021-01-01'
ORDER BY hire_date, salary DESC;
```

### Sales: Top performers by region
```sql
SELECT name, city, salary, department
FROM employees 
WHERE department IN ('Sales', 'Marketing') 
  AND salary > 60000
ORDER BY city, salary DESC 
LIMIT 10;
```

### Inventory: Low stock alerts
```sql
SELECT name, category, price, stock 
FROM products 
WHERE stock <= 100 AND price > 50
ORDER BY stock ASC, price DESC;
```

### Payroll: Department salary analysis
```sql
SELECT name, department, salary,
       CASE 
         WHEN salary > 80000 THEN 'High'
         WHEN salary > 60000 THEN 'Medium' 
         ELSE 'Low' 
       END AS salary_band
FROM employees 
WHERE department NOT IN ('HR')
ORDER BY department, salary DESC;
```


