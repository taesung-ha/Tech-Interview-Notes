# ❌ SQL Mistake Log (LeetCode & StrataScratch)

This is a growing log of SQL mistakes.  
Each entry includes what went wrong, the correct query or logic, missed function, and key learning.

---

## 🧪 [1] Problem: Rising Temperature (LeetCode 197)  
🔗 https://leetcode.com/problems/rising-temperature/  
📄 Table: `Weather`

**❌ Mistake:**  
Tried to subtract dates directly instead of joining.

**✅ Fix:**
Use self-join with `DATEDIFF = 1`.

```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON DATEDIFF(w1.recordDate, w2.recordDate) = 1
WHERE w1.temperature > w2.temperature;
```
### 📌 Missed Concept:

- `DATEDIFF()` returns the number of days between two dates

- Self joins help compare rows across time

### 💡 Insight:
Temporal comparisons in SQL often require joining table to itself.

---

## 🧪 [2] Problem: Most Frequent Employee (StrataScratch)
🔗 https://leetcode.com/problems/rising-temperature/  
📄 Table: `employee_checkin`

**❌ Mistake:**  
Tried to subtract dates directly instead of joining.

**✅ Fix:**
Use self-join with `DATEDIFF = 1`.

```sql
SELECT employee_id, COUNT(*) AS visits
FROM employee_checkin
GROUP BY employee_id
ORDER BY visits DESC
LIMIT 1;
```
### 📌 Missed Concept:

- Aggregation requires explicit `GROUP BY`

- `ORDER BY` + `LIMIT` combo is essential to get "top N"

### 💡 Insight:
Whenever you use aggregation functions, check whether `GROUP BY` is needed.
