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

**Mistake:** Brute-force all subarrays → TLE  
**Fix:** Use Kadane's Algorithm

```python
max_sum = curr = nums[0]
for n in nums[1:]:
    curr = max(n, curr + n)
    max_sum = max(max_sum, curr)
