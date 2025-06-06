# ❌ SQL Mistake Log (LeetCode & StrataScratch)

This is a growing log of SQL mistakes.  
Each entry includes what went wrong, the correct query or logic, missed function, and key learning.

---

## 🧪 [1] Problem: Rising Temperature (LeetCode 197)  
🔗 https://leetcode.com/problems/rising-temperature/  
📄 Table: `Weather`

**❌ Mistake:**  
attempted to use a join without realizing that the `DATEDIFF` function was needed to calculate the difference between dates.

**✅ Fix:**  
Use self-join with `DATEDIFF = 1`.

```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON DATEDIFF(w1.recordDate, w2.recordDate) = 1
WHERE w1.temperature > w2.temperature;
```
**📌 Missed Concept:**

- `DATEDIFF()` returns the number of days between two dates

- Self joins help compare rows across time

**💡 Insight:**  
Temporal comparisons in SQL often require joining table to itself.

---

## 🧪 [2] Problem: Average Time of Process per Machine (LeetCode 1661)
🔗 https://leetcode.com/problems/average-time-of-process-per-machine/description/?envType=study-plan-v2&envId=top-sql-50  
📄 Table: `Activity`

**❌ Mistake:**  
failed to consider preprocessing by joining the table itself using `on` condition, and instead tried to split the table using `WHERE` clause, which made the code unnecessarily complicated.

**✅ Fix:**  
Use self-join with multiple `on` conditions.

```sql
SELECT a1.machine_id, round(avg(a2.timestamp-a1.timestamp),3) as processing_time
FROM Activity as a1
JOIN Activity as a2
ON a1.machine_id = a2.machine_id
AND a1.process_id = a2.process_id
AND a1.activity_type = 'start'
AND a2.activity_type = 'end'
GROUP BY machine_id
```
**📌 Missed Concept:**

- self `join` method
- multiple `on` conditions

**💡 Insight:**  
Whenever you want to separate multiple states and perform cacluation for each row accordingly, you don't need to split the table. It's possible using a `self-join` and multiple `on` condtions.

---

## 🧪 [3] Problem: Students and Examinations (LeetCode 1280)
🔗 https://leetcode.com/problems/students-and-examinations/description/?envType=study-plan-v2&envId=top-sql-50  
📄 Table: `Students`

**❌ Mistake:**  
Tried to create a table of every students with every subject **without** using `CROSS JOIN` function. 

**✅ Fix:**  
Use `CROSS JOIN` to create a table of every students with every subject

```sql
WITH subjects_with_students AS (SELECT * FROM Students CROSS JOIN Subjects)
SELECT ss.student_id, ss.student_name, ss.subject_name, count(e.student_id) AS attended_exams
FROM subjects_with_students as ss
LEFT JOIN Examinations as e
ON ss.student_id = e.student_id
AND ss.subject_name = e.subject_name
GROUP BY ss.student_id, ss.subject_name
ORDER BY ss.student_id
```
**📌 Missed Concept:**
- `CROSS JOIN` function

**💡 Insight:**  
When you want to create a table that represents **every field with every other fields**, use a `CROSS JOIN` function.