# 📘 SQL JOINS – Complete Guide

---

## ✅ What is a JOIN?

In SQL, **JOINs** are used to combine rows from **two or more tables** based on a related column between them (usually a **foreign key**).

---

## 🔄 Types of JOINS in SQL (with Use Cases)

| JOIN Type           | Description                                                | Supported in MySQL         |
| ------------------- | ---------------------------------------------------------- | -------------------------- |
| **INNER JOIN**      | Returns only matching rows from both tables                | ✅ Yes                      |
| **LEFT JOIN**       | Returns all rows from the left table + matching from right | ✅ Yes                      |
| **RIGHT JOIN**      | Returns all rows from the right table + matching from left | ✅ Yes                      |
| **FULL OUTER JOIN** | Returns all rows when there's a match in either table      | ❌ *Not supported natively* |
| **CROSS JOIN**      | Returns **cartesian product** (all combinations)           | ✅ Yes                      |
| **SELF JOIN**       | Joins a table with itself                                  | ✅ Yes                      |

---

## 📦 Example Schema: Customers and Orders

We'll use the following two tables:

### 🧑 `customers` Table

| customer\_id | name    | city      |
| ------------ | ------- | --------- |
| 1            | Alice   | Delhi     |
| 2            | Bob     | Mumbai    |
| 3            | Charlie | Bangalore |
| 4            | David   | Delhi     |

---

### 📦 `orders` Table

| order\_id | customer\_id | product | amount |
| --------- | ------------ | ------- | ------ |
| 101       | 1            | Laptop  | 60000  |
| 102       | 2            | Phone   | 30000  |
| 103       | 1            | Mouse   | 1500   |
| 104       | 3            | Monitor | 12000  |

---

## 💡 1. INNER JOIN

**Returns only those records where there is a match in both tables.**

```sql
SELECT c.name, o.product, o.amount
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```

### 🧾 Output:

| name    | product | amount |
| ------- | ------- | ------ |
| Alice   | Laptop  | 60000  |
| Bob     | Phone   | 30000  |
| Alice   | Mouse   | 1500   |
| Charlie | Monitor | 12000  |

📌 **David** doesn't have any order, so he's not shown.

---

## 💡 2. LEFT JOIN (or LEFT OUTER JOIN)

**Returns all customers and matching orders. If no order, NULL is shown.**

```sql
SELECT c.name, o.product, o.amount
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

### 🧾 Output:

| name    | product | amount |
| ------- | ------- | ------ |
| Alice   | Laptop  | 60000  |
| Alice   | Mouse   | 1500   |
| Bob     | Phone   | 30000  |
| Charlie | Monitor | 12000  |
| David   | NULL    | NULL   |

📌 David is shown even though he has no order.

---

## 💡 3. RIGHT JOIN (or RIGHT OUTER JOIN)

**Returns all orders and matching customers. If no customer, NULL is shown.**

```sql
SELECT c.name, o.product, o.amount
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```

### 🧾 Output:

| name    | product | amount |
| ------- | ------- | ------ |
| Alice   | Laptop  | 60000  |
| Bob     | Phone   | 30000  |
| Alice   | Mouse   | 1500   |
| Charlie | Monitor | 12000  |

 Same as INNER JOIN here, because all orders belong to valid customers.

---

##  FULL OUTER JOIN (Not directly supported in MySQL)

But we can **simulate** it using `UNION`:

```sql
SELECT c.name, o.product, o.amount
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id

UNION

SELECT c.name, o.product, o.amount
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```

---

## 💡 4. CROSS JOIN

**Returns all possible combinations between the two tables.**

```sql
SELECT c.name, o.product
FROM customers c
CROSS JOIN orders o;
```

📌 If there are 4 customers and 4 orders → **4 × 4 = 16 rows**

---

## 💡 5. SELF JOIN

Use when you need to compare rows within the same table.

### Example: Get all customers from the same city (excluding themselves):

```sql
SELECT A.name AS customer1, B.name AS customer2, A.city
FROM customers A
JOIN customers B ON A.city = B.city AND A.customer_id != B.customer_id;
```

---

## 🧱 Full Table Setup (Run in MySQL)

### 1. Create `customers` Table

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

### 2. Insert into `customers`

```sql
INSERT INTO customers (customer_id, name, city) VALUES
(1, 'Alice', 'Delhi'),
(2, 'Bob', 'Mumbai'),
(3, 'Charlie', 'Bangalore'),
(4, 'David', 'Delhi');
```

---

### 3. Create `orders` Table

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(100),
    amount DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

### 4. Insert into `orders`

```sql
INSERT INTO orders (order_id, customer_id, product, amount) VALUES
(101, 1, 'Laptop', 60000.00),
(102, 2, 'Phone', 30000.00),
(103, 1, 'Mouse', 1500.00),
(104, 3, 'Monitor', 12000.00);
```

---


## 🧠 Summary Table

| JOIN Type       | Use Case Example                         | Includes Non-Matching Rows?   |
| --------------- | ---------------------------------------- | ----------------------------- |
| INNER JOIN      | Customers who placed orders              | ❌ No                          |
| LEFT JOIN       | All customers, with or without orders    | ✅ Yes (left only)             |
| RIGHT JOIN      | All orders, even if customer missing     | ✅ Yes (right only)            |
| FULL OUTER JOIN | All customers and all orders             | ✅ Yes (both sides) (❌ native) |
| CROSS JOIN      | All combinations of customers and orders | ✅ Yes                         |
| SELF JOIN       | Compare rows within the same table       | ✅ Yes                         |

---

