# ❌ SQL Mistake Index (by Topic)

A categorized list of SQL problems I initially got wrong or misunderstood.  
Grouped by concept for quick reference and pattern recognition.

---

## 🟦 JOIN Issues

- Rising Temperature [(LeetCode 197)](https://leetcode.com/problems/rising-temperature/), [[Markdown]](SQL-Mistakes.md#🧪-1-problem-rising-temperature-leetcode-197)

  → Forgot to use self-join to compare consecutive dates.
  

- [Lyft Driver Wages (StrataScratch)](https://platform.stratascratch.com/coding/10308/lyft-driver-wages)  
  → Used default INNER JOIN instead of LEFT JOIN, dropped unmatched rows.

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

- [Top 3 Salaries (LeetCode 177)](https://leetcode.com/problems/nth-highest-salary/)  
  → Used `LIMIT` but forgot about dense rank via `ROW_NUMBER()`.

- [Rolling Revenue (StrataScratch)](https://platform.stratascratch.com/coding/10145/rolling-revenue)  
  → Didn't partition by user, window summed all rows.

---

## 🟩 Subqueries / Filtering

- [Second Highest Salary (LeetCode 176)](https://leetcode.com/problems/second-highest-salary/)  
  → Wrote incorrect subquery with LIMIT 1 and OFFSET but missed `NULL` case.

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
