

##  What is a Clause in SQL?

**Clauses** are parts of SQL statements that perform specific tasks like filtering, sorting, grouping, etc.

---

##  Common SQL Clauses with Examples

We'll use a table named `Employees`:

### Sample Table: `Employees`

| EmployeeID | Name    | Department | Salary | Age |
| ---------- | ------- | ---------- | ------ | --- |
| 101        | Alice   | HR         | 30000  | 25  |
| 102        | Bob     | IT         | 40000  | 30  |
| 103        | Charlie | IT         | 42000  | 35  |
| 104        | David   | HR         | 28000  | 22  |
| 105        | Eva     | Finance    | 50000  | 29  |

---

### 1. **`WHERE` Clause** – filters rows based on condition

```sql
SELECT * FROM Employees
WHERE Department = 'IT';
```

Output: Returns rows where Department is 'IT'.

---

### 2. **`ORDER BY` Clause** – sorts results ascending or descending

```sql
SELECT * FROM Employees
ORDER BY Salary DESC;
```

Output: All employees sorted by salary from highest to lowest.

---

### 3. **`GROUP BY` Clause** – groups rows sharing a value

```sql
SELECT Department, AVG(Salary) AS AvgSalary
FROM Employees
GROUP BY Department;
```

Output: Average salary per department.

---

### 4. **`HAVING` Clause** – filters grouped data (used with `GROUP BY`)

```sql
SELECT Department, COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 1;
```

Output: Shows only departments with more than 1 employee.

---

### 5. **`LIMIT` Clause** – restricts number of rows (works in MySQL, PostgreSQL)

```sql
SELECT * FROM Employees
LIMIT 3;
```

Output: Shows only the first 3 rows.

---

### 6. **`DISTINCT` Clause** – removes duplicate values

```sql
SELECT DISTINCT Department FROM Employees;
```

Output: Shows each department name only once.

---

### 7. **`IN` Clause** – checks if value is in a list

```sql
SELECT * FROM Employees
WHERE Department IN ('HR', 'Finance');
```

Output: Shows employees from HR or Finance departments.

---

### 8. **`BETWEEN` Clause** – checks if value is within a range

```sql
SELECT * FROM Employees
WHERE Age BETWEEN 25 AND 35;
```

Output: Shows employees aged between 25 and 35.

---

### 9. **`LIKE` Clause** – pattern matching (used with wildcards)

```sql
SELECT * FROM Employees
WHERE Name LIKE 'A%';
```

Output: Names starting with 'A' (e.g., Alice).


