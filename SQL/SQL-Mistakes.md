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

---

## 🧪 [4] Problem: Salaries Differences
🔗 https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=1  
📄 Table: `db_employee`, `db_dept`

**❌ Mistake:**  
failed to calculate the salary difference between the first and second rows. 

**✅ Fix:**  
Use `LIMIT 1` and `LIMIT 1 OFFSET 1` to calculate the difference between the first and second rows. 

```sql
select
(select
    max(e.salary)
from
    db_employee as e
left join
    db_dept as d
on
    e.department_id = d.id
where
    d.department = 'engineering' or d.department = 'marketing'
group by
    d.department
limit 1
offset 1)
```
**📌 Missed Concept:**
- `LIMIT 1`, `OFFSET 1` function

**💡 Insight:**  
When you want to calculate the difference between first two rows, use `LIMIT 1` and `OFFSET 1`.

---

## 🧪 [5] Users By Average Session Time
🔗 https://platform.stratascratch.com/coding/10352-users-by-avg-session-time?code_type=1  
📄 Table: `facebook_web_log`

**❌ Mistake:**  
failed to perform `left join` while preservering the row order of both tables.

**✅ Fix:**  
USE `row_number() over (partition by user_id order by max(timestamp)) as rn`

```sql
with page_load_date as (
select
    user_id,
    max(timestamp),
    row_number () over (partition by user_id order by max(timestamp)) as rn
from
    facebook_web_log
where
    action = 'page_load'
group by
    user_id, date(timestamp)
),
page_exit_date as (
select
    user_id,
    min(timestamp),
    row_number () over (partition by user_id order by min(timestamp)) as rn
from
    facebook_web_log
where
    action = 'page_exit'
group by
    user_id, date(timestamp)
)

select
    l.user_id,
    avg(e.min - l.max)
from
    page_load_date as l
left join
    page_exit_date as e
on
    l.user_id = e.user_id
and
    l.rn = e.rn
where
    e.min-l.max is not null
group by
    l.user_id
```
**📌 Missed Concept:**
- `row_number()` window function. 

**💡 Insight:**  
Whenever you want to merge the two tables while preserving the original row order, use `row_number()` and define `on` conditions regarding it. 

---

## 🧪 [6] Problem: Ranking Most Active Guests
🔗 https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=2  
📄 Table: `airbnb_contacts`

**❌ Mistake:**  
Forgot how to add rank field.

**✅ Fix:**  
Use `dense_rank over (order by column desc) as rn

```sql
select
    dense_rank() over (order by sum(n_messages) desc) as ranking,
    id_guest,
    sum(n_messages) as sum_n_messages
from
    airbnb_contacts
group by
    id_guest
```
**📌 Missed Concept:**
- `dense_rank() over (order by column desc)`

**💡 Insight:**  
Whenever you want to add rank column without skip any ranking numbers, use `dense_rank() over (order by column asc)`.

---

