
###  Table: `students`

| id | name    | age | grade | city      |
| -- | ------- | --- | ----- | --------- |
| 1  | Ayesha  | 18  | A     | Karachi   |
| 2  | Bilal   | 19  | B     | Lahore    |
| 3  | Ayesha  | 18  | A     | Karachi   |
| 4  | Daniyal | 20  | C     | Islamabad |
| 5  | Fatima  | 21  | B     | Karachi   |
| 6  | Hammad  | 18  | A     | Lahore    |

---

##  1. `UPDATE`: Update Student Info

**Update Fatima’s grade to 'A+'**

```sql
UPDATE students
SET grade = 'A+'
WHERE name = 'Fatima';
```

---

##  2. `DELETE`: Delete Records Using Conditions

**Delete all students from Lahore**

```sql
DELETE FROM students
WHERE city = 'Lahore';
```

>  After this, Bilal and Hammad will be deleted.

---

##  3. `DISTINCT`: Get Unique Names or Cities

**Get unique student names (remove duplicates like Ayesha):**

```sql
SELECT DISTINCT name
FROM students;
```

---

##  4. `LIMIT`: Limit Number of Results

**Get only 3 students from the table:**

```sql
SELECT *
FROM students
LIMIT 3;
```

---

##  5. `ORDER BY`: Sort the Results

**Sort students by age (youngest to oldest):**

```sql
SELECT *
FROM students
ORDER BY age ASC;
```

---

##  6. `OFFSET`: Skip Some Rows

**Get 2 students after skipping the first 2 (for pagination):**

```sql
SELECT *
FROM students
ORDER BY id
LIMIT 2 OFFSET 2;
```

---

##  Combined Example:

Here's a query combining `ORDER BY`, `LIMIT`, and `OFFSET`:

```sql
SELECT *
FROM students
ORDER BY age DESC
LIMIT 2 OFFSET 1;
```

This gets **2 students**, ordered by **age (oldest first)**, **skipping the first**.





### **Questions: SQL Practice on `students` Table**

Assume the `students` table has the following columns:
**id, name, age, grade, city**

---

1. **Update the grade of the student named 'Fatima' to 'A+'.**
   *Write the SQL query to perform this update.*

2. **Delete all students who are from the city 'Lahore'.**
   *Write the SQL query to delete such records.*

3. **Write a query to get a list of unique student names from the table.**
   *Make sure duplicates are not shown.*

4. **Write a query to retrieve only the first 3 records from the students table.**

5. **Sort the students by their age in ascending order and display all the columns.**

6. **Write a query to retrieve 2 students, but skip the first 2 in the result.**
   *Use `LIMIT` and `OFFSET`.*

7. **Combine `ORDER BY`, `LIMIT`, and `OFFSET` to get 3 students sorted by age in descending order, skipping the first one.**

8. **Write a query to delete all students who are older than 20.**

9. **Update the city of the student with `id = 4` to 'Peshawar'.**

10. **Get a list of unique cities from the students table.**
    *Avoid duplicates using the appropriate clause.*


