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

## 🧪 [7] Problem: Ranking Most Active Guests
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

## 🧪 [8] Problem: Aromba-based Winery Search
🔗 https://platform.stratascratch.com/coding/10026-find-all-wineries-which-produce-wines-by-possessing-aromas-of-plum-cherry-rose-or-hazelnut?code_type=2   
📄 Table: `winemag_p1`

**❌ Mistake:**  
Wasn't familiar with regular expression syntax. 

```sql
SELECT *
FROM winemag_p1
WHERE description ~* '\y(plum|cherry|rose|hazelnut)\y'
```

**💡 Insight:**  
Whenever you want to filter data that contains a specific string, use regular expressions. 

---

## 🧪 [9] Problem: Spam Posts
🔗 https://platform.stratascratch.com/coding/10134-spam-posts?code_type=2  
📄 Table: `facebook_posts`, `facebook_post_views`

**❌ Mistake:**  
Didn't realize that explicitly specify the float (or decimal) data type when calculating numbers.

**✅ Fix:**  
Use `cast( as float)` to specify the number as float type. 

```sql
with table1 as (
select 
    *
from 
    facebook_posts as p
left join
    facebook_post_views as v
on
    p.post_id = v.post_id
where
    v.viewer_id is not null
)

select
    sub1.post_date,
    cast(sum(spam) as float) / count(*) * 100 as spam_sphere
from (select
    post_date,
    case
        when post_keywords like '%#spam#%' then 1
        else 0
    end as spam
from
    table1) as sub1
group by
    post_date
```
**📌 Missed Concept:**
- `cast(sum(spam) as float)`

**💡 Insight:**  
In SQL, it's important to explicitly specify the float (or decimal) data type, especially because division operations are often performed using integer-based arithmetic by default. 

---

## 🧪 [10] Problem: Reviews of Categories
🔗 https://platform.stratascratch.com/coding/10049-reviews-of-categories?code_type=2  
📄 Table: `yelp_business`

**❌ Mistake:**  
Didn't know how to split the columns based on the specific string. 

**✅ Fix:**  
Use `unnest(string_to_array(categories, ';')`

```sql
select
    unnest(string_to_array(categories, ';')) as category,
    sum(review_count) as review_cnt
from
    yelp_business
group by
    unnest(string_to_array(categories, ';'))
order by 
    sum(review_count) desc
```
**📌 Missed Concept:**
- `unnest(string_to_array(categories, ';')`

**💡 Insight:**  
If a column contains multiple values concatenated together, first use `string_to_array` to split them, and then use `unnest` to separate them into individual rows.

---

## 🧪 [11] Users By Average Session Time
🔗 https://platform.stratascratch.com/coding/2007-rank-variance-per-country?python=&utm_source=youtube&utm_medium=click&utm_campaign=YT+description+link&code_type=1  
📄 Table: `fb_comments_count`, `fb_active_users`

**❌ Mistake:**  
Failed to convert date column into the desired string format since `date_format` does not work in PostSQL.

**✅ Fix:**  
USE `to_char(column, 'YYYY-mm')`

```sql
with t2019_12 as (
select 
    sum(fcc.number_of_comments) as total_number,
    fau.country,
    dense_rank() over (order by sum(fcc.number_of_comments) desc)
from 
    fb_comments_count as fcc
left join
    fb_active_users as fau
on
    fcc.user_id = fau.user_id
where
    to_char(fcc.created_at,'YYYY-mm') = '2019-12' and fau.country is not null
group by
    fau.country)
, 
t2020_01 as (
select 
    sum(fcc.number_of_comments) as total_number,
    fau.country,
    dense_rank() over (order by sum(fcc.number_of_comments) desc)
from 
    fb_comments_count as fcc
left join
    fb_active_users as fau
on
    fcc.user_id = fau.user_id
where
    to_char(fcc.created_at,'YYYY-mm') = '2020-01' and fau.country is not null
group by
    fau.country
)

select
    t2019_12.country
from
    t2019_12
left join
    t2020_01
on
    t2019_12.country = t2020_01.country
where
    t2019_12.dense_rank > t2020_01.dense_rank

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
- `to_char(fcc.created_at, 'YYYY-mm') = `

**💡 Insight:**  
Whenever you want to convert date column(ex. YYYY-MM-DD) into the desired string format like 'YYYY-MM', especially in PostgreSQL, use `to_char(date_column, 'YYYY-mm')`.

---

## 🧪 [12] Top Percentile Fraud
🔗 https://platform.stratascratch.com/coding/10303-top-percentile-fraud?code_type=2
📄 Table: `fraud_score`

**❌ Mistake:**  
Didn't know how to calculate the top 5 perentile of claims with the highest fraud scores. 

**✅ Fix:**  
Use `percentile_cont(0.95) within group (order by fraud_score)`

```sql
with percentile as (
select 
    state,
    percentile_cont(0.95) within group (order by fraud_score) as threshold
from 
    fraud_score
group by
    state
)

select
    fs.policy_num,
    fs.state,
    fs.claim_cost,
    fs.fraud_score
from
    fraud_score as fs
left join
    percentile as p
on
    fs.state = p.state
where
    fs.fraud_score >= p.threshold
```
**📌 Missed Concept:**

- `percentile_cont(0.95) within group (order by)`

**💡 Insight:**  
To calculate the percentile for some column within group, use `percentile_cont(0.95) within group (order by)`

---

## 🧪 [13] Problem: Largest Olympics
🔗 https://platform.stratascratch.com/coding/9942-largest-olympics?code_type=1 
📄 Table: `olympics_athletes_events`

**❌ Mistake:**  
failed to count distinct values for the number of atheletes. 

**✅ Fix:**  
Use `count(distinct id)` to count the distinct number of people. 

```sql
select 
    games,
    count(distinct id) as athletes_count
from  
    olympics_athletes_events 
group by
    games
order by 
    count(distinct id) desc
limit 1;
```
**📌 Missed Concept:**

- Way to count distinct number. 

---

## 🧪 [14] Best Selling Item
🔗 https://platform.stratascratch.com/coding/10172-best-selling-item?code_type=1  
📄 Table: `fraud_score`  

**❌ Mistake:**  
Forgot how to keep only the month from a date. 

**✅ Fix:**  
Use `to_char(date, 'MM')`

```sql
WITH table1 as (
SELECT 
    to_char(invoicedate, 'MM') AS month,
    description,
    sum(quantity*unitprice) AS total_paid
FROM 
    online_retail
GROUP BY
    month, description
ORDER BY
    month)

SELECT
    table1.month,
    table1.description,
    table2.total_paid
FROM (SELECT
    month,
    max(total_paid) AS total_paid
FROM
    table1
GROUP BY
    month) AS table2
LEFT JOIN
    table1
ON
    table1.month = table2.month
AND
    table1.total_paid = table2.total_paid

```
**📌 Missed Concept:**

- `to_char(date, 'MM')`

**💡 Insight:**  
To change the date format, use `to_char` in postgreSQL. 