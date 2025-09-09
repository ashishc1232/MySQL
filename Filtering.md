

#  **Day 2: Data Filtering in SQL**

---

## 🧠 **Theory Concepts**

### 🔹 1. `WHERE` Clause:

`WHERE` ka use **table se specific rows filter karne** ke liye hota hai — jahan condition match ho.

```sql
SELECT * FROM students WHERE age > 18;
```

> 🔍 Yani sirf un students ke records dikhaye jinka `age` 18 se zyada ho.

---

### 🔹 2. **Operators**

| Operator  | Use / Meaning                 | Example                             |
| --------- | ----------------------------- | ----------------------------------- |
| `=`       | Equal to                      | `WHERE age = 18`                    |
| `>`       | Greater than                  | `WHERE marks > 75`                  |
| `<`       | Less than                     | `WHERE age < 20`                    |
| `BETWEEN` | Range check                   | `WHERE marks BETWEEN 60 AND 80`     |
| `IN`      | Multiple value match          | `WHERE city IN ('Delhi', 'Mumbai')` |
| `LIKE`    | Pattern match (for strings)   | `WHERE name LIKE 'A%'`              |
| `NOT`     | Negation (not this condition) | `WHERE NOT age = 18`                |

---

### 🔹 3. `ORDER BY` Clause

Data ko **sort karne ke liye** use hota hai — ascending ya descending order mein.

```sql
SELECT * FROM students ORDER BY age ASC;  -- Chhoti age se badi age tak
SELECT * FROM students ORDER BY marks DESC; -- Highest marks first
```

---

## 🗃️ **Sample `students` Table**

| id | name   | age | city   | marks |
| -- | ------ | --- | ------ | ----- |
| 1  | Aman   | 17  | Delhi  | 78    |
| 2  | Priya  | 19  | Mumbai | 88    |
| 3  | Rahul  | 18  | Jaipur | 65    |
| 4  | Anjali | 20  | Delhi  | 92    |
| 5  | Karan  | 18  | Pune   | 55    |

---

## 🛠️ **Practice Examples**

### 🔸 1. Students jinka age > 18 ho:

```sql
SELECT * FROM students
WHERE age > 18;
```

➡️ Output: Anjali (age 20), Priya (age 19)

---

### 🔸 2. Students jinka city "Delhi" ho:

```sql
SELECT * FROM students
WHERE city = 'Delhi';
```

➡️ Output: Aman, Anjali

---

### 🔸 3. Students with marks BETWEEN 60 and 90:

```sql
SELECT * FROM students
WHERE marks BETWEEN 60 AND 90;
```

➡️ Output: Aman, Priya, Rahul

---

### 🔸 4. Students from Delhi or Pune:

```sql
SELECT * FROM students
WHERE city IN ('Delhi', 'Pune');
```

➡️ Output: Aman, Anjali, Karan

---

### 🔸 5. Students jinka naam "A" se start hota ho:

```sql
SELECT * FROM students
WHERE name LIKE 'A%';
```

➡️ Output: Aman, Anjali

---

### 🔸 6. Students jinka age 18 **nahi** hai:

```sql
SELECT * FROM students
WHERE NOT age = 18;
```

➡️ Output: Aman (17), Priya (19), Anjali (20)

---

### 🔸 7. Students ko marks ke descending order mein dikhana:

```sql
SELECT * FROM students
ORDER BY marks DESC;
```

➡️ Output: Anjali, Priya, Aman, Rahul, Karan

---

Task:
Perfect! 👏
Yah rahe **10 practical SQL questions** on **Data Filtering** (Day 2 concepts), jo beginner students **easily samajh aur solve** kar sakte hain — with realistic examples based on the `students` table.

---

## 📄 **Sample `students` Table (Same as Before)**

| id | name   | age | city   | marks |
| -- | ------ | --- | ------ | ----- |
| 1  | Aman   | 17  | Delhi  | 78    |
| 2  | Priya  | 19  | Mumbai | 88    |
| 3  | Rahul  | 18  | Jaipur | 65    |
| 4  | Anjali | 20  | Delhi  | 92    |
| 5  | Karan  | 18  | Pune   | 55    |

---

## 🧪 **10 SQL Practice Questions — Data Filtering**

---

### **Q1.** Get details of all students who are older than 18.

```sql
SELECT * FROM students
WHERE age > 18;
```

---

### **Q2.** Show all students who scored **less than or equal to 70 marks**.

```sql
SELECT * FROM students
WHERE marks <= 70;
```

---

### **Q3.** Find students **exactly 18 years old**.

```sql
SELECT * FROM students
WHERE age = 18;
```

---

### **Q4.** Show students whose `city` is either **Delhi** or **Mumbai**.

```sql
SELECT * FROM students
WHERE city IN ('Delhi', 'Mumbai');
```

---

### **Q5.** Get names of students whose `name` starts with **"A"**.

```sql
SELECT name FROM students
WHERE name LIKE 'A%';
```

---

### **Q6.** Show students whose marks are **between 60 and 90**.

```sql
SELECT * FROM students
WHERE marks BETWEEN 60 AND 90;
```

---

### **Q7.** List students who are **not from Delhi**.

```sql
SELECT * FROM students
WHERE city != 'Delhi';
-- or
-- WHERE NOT city = 'Delhi';
```

---

### **Q8.** Display all students ordered by `marks` in **descending order** (highest first).

```sql
SELECT * FROM students
ORDER BY marks DESC;
```

---

### **Q9.** Show students who are **18 years old** and from **Pune**.

```sql
SELECT * FROM students
WHERE age = 18 AND city = 'Pune';
```

---

### **Q10.** Find all students whose names contain the letter **'a'** (any position, case-insensitive).

```sql
SELECT * FROM students
WHERE name LIKE '%a%';
```

---



