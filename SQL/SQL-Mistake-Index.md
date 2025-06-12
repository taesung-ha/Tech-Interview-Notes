# ❌ SQL Mistake Index (by Topic)

A categorized list of SQL problems I initially got wrong or misunderstood.  
Grouped by concept for quick reference and pattern recognition.

---

## 🟦 JOIN Issues

- [Rising Temperature (LeetCode 197)](https://leetcode.com/problems/rising-temperature/) [[Go to mistake]](SQL-Mistakes.md#-1-problem-rising-temperature-leetcode-197)  
  → Forgot to use self-join to compare consecutive dates.
  

- [Average Time of Process per Machine (LeetCode 1661)](https://leetcode.com/problems/average-time-of-process-per-machine/description/?envType=study-plan-v2&envId=top-sql-50) [[Go to mistake]](SQL-Mistakes.md#-2-problem-average-time-of-process-per-machine-leetcode-1661)  
  → Forgot to use mulitle `on` conditions for preprocessing.

- [Students and Examinations (LeetCode 1280)](https://leetcode.com/problems/students-and-examinations/description/?envType=study-plan-v2&envId=top-sql-50) [[Go to mistake]](SQL-Mistakes.md#-3-problem-students-and-examinations-leetcode-1280)  
  → Didn't know about using `CROSS JOIN`.

---

## 🟨 GROUP BY / Aggregation Mistakes

- [Most Frequent Employee (StrataScratch)](https://platform.stratascratch.com/coding/9782/find-the-most-frequent-employees)  
  → Tried COUNT(*) without GROUP BY → only one row returned.

- [Class Performance (LeetCode)](https://leetcode.com/problems/classes-more-than-5-students/)  
  → Missed filtering after aggregation (HAVING vs WHERE confusion).

---

## 🟪 Date & Time Functions

- [User Retention (StrataScratch)](https://platform.stratascratch.com/coding/9632/user-retention)  
  → Tried filtering string dates; forgot `DATE()` or conversion.

- [Average Daily Sales (Custom)](https://platform.stratascratch.com/coding/12345/avg-daily-sales)  
  → Grouped by `created_at` without truncating to day.

---

## 🟥 Window Functions

- [Users By Average Session Time](https://platform.stratascratch.com/coding/10352-users-by-avg-session-time?code_type=1)  
  → failed to perform `left join` while preservering the row order of both tables.

- [Rolling Revenue (StrataScratch)](https://platform.stratascratch.com/coding/10145/rolling-revenue)  
  → Didn't partition by user, window summed all rows.

- [Ranking Most Active Guests](https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=2)  
  → Forgot how to add rank field.

---

## 🟩 Subqueries / Filtering

- [Salaries Differences](https://leetcode.com/problems/second-highest-salary/)  
  → Failed to calculate the salary difference between the first and second rows.

- [Duplicate Emails (LeetCode 196)](https://leetcode.com/problems/duplicate-emails/)  
  → Used `WHERE` without GROUP BY HAVING COUNT > 1.

---

## 🟫 Miscellaneous

- [Big Countries (LeetCode 595)](https://leetcode.com/problems/big-countries/)  
  → Missed that OR logic was required for two conditions.

---

## 🧠 Tip
Use this index to:
- Identify repeated patterns in mistakes
- Review one topic at a time before interviews
- Prioritize practice (e.g., joins → window → subqueries)

For full explanations, see `SQL-Mistakes.md`.
