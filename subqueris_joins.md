

| SaleID | SalesPerson | Region | Amount |
| ------ | ----------- | ------ | ------ |
| 1      | Amit        | North  | 5000   |
| 2      | Neha        | South  | 7000   |
| 3      | Amit        | North  | 3000   |
| 4      | Neha        | South  | 4000   |
| 5      | Raj         | East   | 2500   |
| 6      | Amit        | North  | 6000   |
| 7      | Raj         | East   | 1500   |
| 8      | Simran      | West   | 8000   |
| 9      | Simran      | West   | 5500   |
| 10     | Neha        | South  | 3000   |

---

# 🔍 1. Subquery Example

### 🎯 Q: **Salespersons who have total sales above average sales.**

```sql
SELECT SalesPerson, SUM(Amount) AS TotalSales
FROM Sales
GROUP BY SalesPerson
HAVING SUM(Amount) > (
    SELECT AVG(Amount) FROM Sales
);
```

🧠 Yahan:

* Subquery `(SELECT AVG(Amount)...)` pehle overall average sale nikaalegi.
* `HAVING` us average se zyada total sales wale SalesPerson ko dikhayega.

---

# 🔗 2. JOIN Example

### 🎯 Suppose humare paas ek aur table hai: `Regions`

```sql
CREATE TABLE Regions (
    Region VARCHAR(30) PRIMARY KEY,
    Manager VARCHAR(50)
);

INSERT INTO Regions VALUES
('North', 'Manoj'),
('South', 'Rita'),
('East', 'Deepak'),
('West', 'Sonal');
```

---

### 🔄 Now: **Join both tables to show each sale with Region Manager**

```sql
SELECT S.SalesPerson, S.Region, S.Amount, R.Manager
FROM Sales S
JOIN Regions R ON S.Region = R.Region;
```

🧠 Explanation:

* `JOIN` karta hai `Sales` aur `Regions` ko
* `ON` condition ke through matching `Region` ke basis pe

---

# 🧪 3. Correlated Subquery Example

### 🎯 Q: **Show all sales where the amount is greater than that salesperson’s average sale.**

```sql
SELECT *
FROM Sales S1
WHERE Amount > (
    SELECT AVG(Amount)
    FROM Sales S2
    WHERE S1.SalesPerson = S2.SalesPerson
);
```

🧠 Yahan:

* Har row ke liye `SalesPerson` ka average calculate hota hai (inside subquery)
* Fir outer query sirf unhi rows ko dikhati hai jahan amount > uska average hai

---

# 🎯 4. Common Table Expression (CTE)

### 🔄 CTE se readable query likhna:

```sql
WITH TotalSales AS (
    SELECT SalesPerson, SUM(Amount) AS TotalAmount
    FROM Sales
    GROUP BY SalesPerson
)
SELECT * FROM TotalSales
WHERE TotalAmount > 9000;
```

🧠 `WITH` clause ek temporary result (CTE) banata hai jo baad me use hota hai.

---

# ✅ Summary

| Technique               | Use Case                                       |
| ----------------------- | ---------------------------------------------- |
| **Subquery**            | Query inside another query                     |
| **JOIN**                | Combine data from multiple tables              |
| **Correlated Subquery** | Inner query depends on outer query row         |
| **CTE (`WITH`)**        | Clean and modular way to write complex queries |

---


