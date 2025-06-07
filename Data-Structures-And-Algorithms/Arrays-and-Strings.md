# 📘 Arrays and Strings

## ✅ Summary
- Python uses `list` instead of traditional arrays.
- Strings are **immutable** in Python — modifying them means creating a new one.
- Two pointers just refers to using two integer variables to move along some iterables. 

---

## 🔁 Common Patterns

---

## 🔹 Pattern 1: Two Pointers

| Item               | Description |
|--------------------|-------------|
| **Core Idea**       | Start the pointers at the edge of the input. Move them towards each other until they meet. ***Note: two pointers do not always mean that left and right. It also can be i, j for arr1, arr2.**|
| **Strength**     | Never have more than O(n) iterations for the while loop. |
| **Typical Use Cases** | Max/min subarray length, unique element window, averages |
| **Common Mistakes** | Forgetting to shrink window properly, not resetting running sums |
| **Python Tips**     | Use `while` with `left<right` condition. 
| **Sample Code**     |

```python
left = 0
right = len(arr)-1

while left < right:
    Do some logic here depending on the problem
    Do some more logic here to decide on one of the following:
        1. left ++
        2. right --
        3. Both left += and right --
```

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