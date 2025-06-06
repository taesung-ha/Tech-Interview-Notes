# 📘 Array

## ✅ Summary
- Arrays store elements in contiguous memory with O(1) access.
- Common use cases: search, sliding window, prefix sums, two pointers.

## 🔁 Common Patterns

| Pattern        | Example Problem         | Description                         |
|----------------|--------------------------|-------------------------------------|
| Sliding Window | LeetCode 209             | Maintain a moving window            |
| Two Pointers   | LeetCode 26              | Use two indices to track conditions |
| Prefix Sum     | LeetCode 560             | Store cumulative sums               |

## 🧠 Edge Cases & Mistakes
- Off-by-one errors
- Forgetting to reset state
- Overflow in sum calculations

## 💡 Tips
- Use `enumerate()` for index-value pairing in Python
- Watch out for constraints like "in-place"

## 🧪 Mistake Log

### ❌ LeetCode 53 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.

```python
max_sum = curr = nums[0]
for n in nums[1:]:
    curr = max(n, curr + n)
    max_sum = max(max_sum, curr)
```
### 📌 Missed Function:
`pd.merge()` Combines two DataFrames. Default `how='inner'` may drop rows.
Set `how='left'` to preserve all from the left.

### 💡 Insight:
Never assume the default behavior of joins. Always write how= explicitly.

---

### ❌ LeetCode 52 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.