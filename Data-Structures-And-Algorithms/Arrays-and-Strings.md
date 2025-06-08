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
| **Typical Use Cases** | Palindrome, Two Sum(Input array is sorted), Is Subsequence|
| **Common Mistakes** |  |
| **Python Tips**     | Use `while` with `left<right` condition 
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
- 
- 
- 

## 💡 Tips
- 
- 

---

## 🔹 Pattern 2: Sliding Window

| Item               | Description |
|--------------------|-------------|
| **Core Idea**       | Sliding window is used to analyze and find **the valid subarrays** of an array.|
| **Strength**     | any alogrithms that looks at every subarray will be at least O($n^2$). But sliding window guarantees a maximum of O($2n$) -> O($n$) window iterations - the right pointer and left pointer can move n each times, which is much faster.|
| **Typical Use Cases** | Max/min subarray length, unique element window, averages |
| **Common Mistakes** | Forgetting that a while loop can be used similarly to an `if` statement - if the condition is not met, the loop is skipped and the program moves on to the next line of code. |
| **Python Tips**     | (1) Use a for loop to iterate `right` over the input, and `while curr > k` (while the window is invalid) to increment `left` (2) Identify **constraint metric** by calling `curr`. 
| **Sample Code**     |

```python
def fn(nums, k):
    left = curr = ans = 0
    for right < len(nums):
        curr += nums[right]
        while curr > k:
            curr -= nums[left]
            left += 1
        ans = max(ans, right - left + 1)
    
    return answer
```

## 🧠 Edge Cases & Mistakes
- Off-by-one errors
- Forgetting to reset state
- Overflow in sum calculations

## 💡 Tips
- Use `enumerate()` for index-value pairing in Python
- Watch out for constraints like "in-place"

## 🧪 Mistake Log

### ❌ LeetCode - Fixed Window Size
🔗 https://leetcode.com/explore/interview/card/leetcodes-interview-crash-course-data-structures-and-algorithms/703/arraystrings/4502/  

**❌ Mistake:**  
Used `sum()` without updating `cur`, resulting a higher time complexity

**✅ Fix:**  
Split the process into two parts: first, directly comput the summation for the fixed-length window of size from index 0 to k-1; then, slide the window one element at a time and update the answer accordingly. 

```python
def find_best_subarray(nums, k):
    curr = 0
    for i in range(k):
        curr += nums[i]
    
    ans = curr
    for i in range(k, len(nums)):
        curr += nums[i] - nums[i - k]
        ans = max(ans, curr)
    
    return ans
```

### 💡 Insight:  
To achieve O(1) time complexity, avoid using the `sum()` function and instead update the answer incrementally at each step. 

---

### ❌ LeetCode 52 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.