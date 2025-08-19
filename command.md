# 📌 **SQL Command Categories**

## 1️⃣ **DDL – Data Definition Language**

* Used to **define or change the structure** of database objects (tables, schemas, indexes).
* **Keywords**: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME`

👉 Examples:

```sql
-- Create Table
CREATE TABLE Employee (
   EmpID INT PRIMARY KEY,
   Name VARCHAR(50),
   Salary DECIMAL(10,2)
);

-- Add a new column
ALTER TABLE Employee ADD Department VARCHAR(30);

-- Delete table permanently
DROP TABLE Employee;

-- Remove all rows but keep structure
TRUNCATE TABLE Employee;

-- Rename table
ALTER TABLE Employee RENAME TO Staff;
```

---

## 2️⃣ **DML – Data Manipulation Language**

* Used to **manipulate (change) data** in tables.
* **Keywords**: `INSERT`, `UPDATE`, `DELETE`, `MERGE`

👉 Examples:

```sql
-- Insert record
INSERT INTO Employee (EmpID, Name, Salary, Department)
VALUES (101, 'Amit', 50000, 'IT');

-- Update salary
UPDATE Employee SET Salary = 60000 WHERE EmpID = 101;

-- Delete record
DELETE FROM Employee WHERE EmpID = 101;
```

---

## 3️⃣ **DQL – Data Query Language**

* Used to **fetch/query data** from database.
* **Keyword**: `SELECT`

👉 Examples:

```sql
-- Select all records
SELECT * FROM Employee;

-- Filter records
SELECT Name, Salary FROM Employee WHERE Department = 'IT';

-- Sort
SELECT * FROM Employee ORDER BY Salary DESC;
```

---

## 4️⃣ **DCL – Data Control Language**

* Used to **control access/permissions** on database.
* **Keywords**: `GRANT`, `REVOKE`

👉 Examples:

```sql
-- Grant SELECT to user
GRANT SELECT ON Employee TO User1;

-- Revoke permission
REVOKE SELECT ON Employee FROM User1;
```

---

## 5️⃣ **TCL – Transaction Control Language**

* Used to **manage transactions** in database (commit, rollback).
* **Keywords**: `COMMIT`, `ROLLBACK`, `SAVEPOINT`

👉 Examples:

```sql
-- Start transaction
BEGIN;

-- Insert record
INSERT INTO Employee VALUES (102, 'Neha', 45000, 'HR');

-- Savepoint (mark point in transaction)
SAVEPOINT before_update;

-- Update record
UPDATE Employee SET Salary = 48000 WHERE EmpID = 102;

-- Rollback to savepoint
ROLLBACK TO before_update;

-- Finalize changes
COMMIT;
```

---

# 📌 **Quick Summary Table**

| Category | Full Form                    | Purpose                 | Examples                        |
| -------- | ---------------------------- | ----------------------- | ------------------------------- |
| **DDL**  | Data Definition Language     | Structure of DB objects | `CREATE, ALTER, DROP, TRUNCATE` |
| **DML**  | Data Manipulation Language   | Manipulate table data   | `INSERT, UPDATE, DELETE`        |
| **DQL**  | Data Query Language          | Query/fetch data        | `SELECT`                        |
| **DCL**  | Data Control Language        | Permissions & access    | `GRANT, REVOKE`                 |
| **TCL**  | Transaction Control Language | Manage transactions     | `COMMIT, ROLLBACK, SAVEPOINT`   |

---

👉 In **real-world projects**:

* DDL = Designing tables
* DML = Adding/updating data
* DQL = Reading reports
* DCL = Managing security
* TCL = Ensuring safe transactions

---

