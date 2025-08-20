

# 📌 Step 1: **Create Table**

```sql
CREATE TABLE Employee (
   EmpID INT PRIMARY KEY,
   Name VARCHAR(50),
   Department VARCHAR(30),
   Salary DECIMAL(10,2)
);
```

✔ Creates a table named **Employee** with 4 columns.

---

# 📌 Step 2: **Insert Records**

```sql
INSERT INTO Employee (EmpID, Name, Department, Salary)
VALUES 
(101, 'Amit', 'IT', 50000),
(102, 'Neha', 'HR', 45000),
(103, 'Rajesh', 'IT', 60000),
(104, 'Priya', 'Finance', 55000);
```

✔ Data inside table now:

| EmpID | Name   | Department | Salary |
| ----- | ------ | ---------- | ------ |
| 101   | Amit   | IT         | 50000  |
| 102   | Neha   | HR         | 45000  |
| 103   | Rajesh | IT         | 60000  |
| 104   | Priya  | Finance    | 55000  |

---

# 📌 Step 3: **Update Records**

```sql
-- Increase salary of Rajesh
UPDATE Employee 
SET Salary = 65000 
WHERE EmpID = 103;

-- Change department of Neha
UPDATE Employee
SET Department = 'Admin'
WHERE EmpID = 102;
```

✔ Updated Table:

| EmpID | Name   | Department | Salary |
| ----- | ------ | ---------- | ------ |
| 101   | Amit   | IT         | 50000  |
| 102   | Neha   | Admin      | 45000  |
| 103   | Rajesh | IT         | 65000  |
| 104   | Priya  | Finance    | 55000  |

---

# 📌 Step 4: **Delete Records**

```sql
-- Delete Priya's record
DELETE FROM Employee WHERE EmpID = 104;
```

✔ Table after delete:

| EmpID | Name   | Department | Salary |
| ----- | ------ | ---------- | ------ |
| 101   | Amit   | IT         | 50000  |
| 102   | Neha   | Admin      | 45000  |
| 103   | Rajesh | IT         | 65000  |

---

# 📌 Step 5: **Other Useful Operations**

### 👉 Select All

```sql
SELECT * FROM Employee;
```

### 👉 Filter (Where Condition)

```sql
SELECT * FROM Employee WHERE Department = 'IT';
```

### 👉 Sort (Order By)

```sql
SELECT * FROM Employee ORDER BY Salary DESC;
```



 




