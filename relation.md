#  **1. Primary Key**

* **Definition**: A column (or combination) that **uniquely identifies each row** in a table.
* **Rules**:

  * Cannot be NULL
  * Must be unique
 Example:

```sql
CREATE TABLE Employee (
   EmpID INT PRIMARY KEY,
   Name VARCHAR(50),
   Department VARCHAR(30)
);
```

 Here `EmpID` is **Primary Key** (unique for every employee).

---

# 📌 **2. Foreign Key**

* **Definition**: A column in one table that refers to the **Primary Key of another table**.
* Ensures **referential integrity** (cannot insert invalid references).

👉 Example:

```sql
CREATE TABLE Department (
   DeptID INT PRIMARY KEY,
   DeptName VARCHAR(30)
);

CREATE TABLE Employee (
   EmpID INT PRIMARY KEY,
   Name VARCHAR(50),
   DeptID INT,
   FOREIGN KEY (DeptID) REFERENCES Department(DeptID)
);
```

✔ Here:

* `DeptID` in **Department** = Primary Key
* `DeptID` in **Employee** = Foreign Key

So an employee **must belong to a valid department**.

---

# 📌 **3. Unique Key**

* Ensures a column’s values are **unique**, but unlike primary key, it **can allow one NULL**.
* Used for columns like PAN, Aadhaar, Passport, VehicleNo.

👉 Example:

```sql
CREATE TABLE Citizen (
   CitizenID INT PRIMARY KEY,
   Name VARCHAR(50),
   AadharNo VARCHAR(12) UNIQUE,
   PAN VARCHAR(10) UNIQUE
);
```

✔ Here:

* `CitizenID` = Primary Key
* `AadharNo`, `PAN` = Unique Keys

---

# 📌 **4. Relationships**

## (a) **One-to-One (1:1)**

* One record in Table A → exactly one record in Table B.

👉 Example:

```sql
CREATE TABLE Employee (
   EmpID INT PRIMARY KEY,
   Name VARCHAR(50)
);

CREATE TABLE EmployeeDetail (
   EmpID INT PRIMARY KEY,
   Address VARCHAR(100),
   PAN VARCHAR(10) UNIQUE,
   FOREIGN KEY (EmpID) REFERENCES Employee(EmpID)
);
```

✔ Each employee has **exactly one detail record**.
(Employee ↔ EmployeeDetail = 1:1)

---

## (b) **One-to-Many (1\:N)**

* One record in Table A → Many records in Table B.

👉 Example: Customer ↔ Orders

```sql
CREATE TABLE Customer (
   CustID INT PRIMARY KEY,
   Name VARCHAR(50)
);

CREATE TABLE Orders (
   OrderID INT PRIMARY KEY,
   CustID INT,
   Product VARCHAR(50),
   FOREIGN KEY (CustID) REFERENCES Customer(CustID)
);
```

✔ One **customer** can have **many orders**.
(Customer ↔ Orders = 1\:N)

---

## (c) **Many-to-Many (M\:N)** (extra info)

* Many records in Table A ↔ Many in Table B.
* Implemented via **junction/bridge table**.

👉 Example: Student ↔ Courses

```sql
CREATE TABLE Student (
   StudentID INT PRIMARY KEY,
   Name VARCHAR(50)
);

CREATE TABLE Course (
   CourseID INT PRIMARY KEY,
   CourseName VARCHAR(50)
);

-- Junction Table
CREATE TABLE StudentCourse (
   StudentID INT,
   CourseID INT,
   PRIMARY KEY (StudentID, CourseID),
   FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
   FOREIGN KEY (CourseID) REFERENCES Course(CourseID)
);
```

✔ One student can take many courses, and one course can have many students.

---

# 📌 **Quick Summary**

| Concept               | Definition                      | Example                           |
| --------------------- | ------------------------------- | --------------------------------- |
| **Primary Key**       | Uniquely identifies row         | `EmpID` in Employee               |
| **Foreign Key**       | Refers to PK of another table   | `DeptID` in Employee → Department |
| **Unique Key**        | Ensures uniqueness, allows NULL | PAN, Aadhaar                      |
| **1:1 Relationship**  | One record ↔ One record         | Employee ↔ EmployeeDetail         |
| **1\:N Relationship** | One record ↔ Many records       | Customer ↔ Orders                 |
| **M\:N Relationship** | Many ↔ Many                     | Student ↔ Course                  |

---

