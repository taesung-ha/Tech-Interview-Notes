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

### ❌ LeetCode 1207 - Unique Number of Occurrences
🔗 https://leetcode.com/problems/unique-number-of-occurrences/description/?envType=study-plan-v2&envId=leetcode-75  

**❌ Mistake:**  
Tried to check whether all elements in the list are unique by implementing for-loop through the list and comparing each element with the wprevious one. 

**✅ Fix:**  
Use `len(set(list)) == len(list)`

```python
len(set(dic.values())) == len(dic.values())
```
**📌 Missed Function:**  
`set(list)` returns the unique value in the list. So if we compare the `len(set(list))` with `len(list)`, then we can check whether all elements in the list are unique. 

**💡 Insight:**  
Comparing the current and previous value in a for loop is not an appropriate method for checking whether all elements in the list are unique. 

---

### ❌ LeetCode 52 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.