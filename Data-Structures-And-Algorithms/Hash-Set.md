# 📘 Hashing

## ✅ Summary
- A hash map is an unordered data structure that stores key-value pairs.  
- In terms of time complexity, hash maps blow arrays out of the water. The following operations are all $O(1)$ for a hash map: 
  - Add an element and associate it with a value.
  - Delete an element if it exists.
  - Check if an element exists.  
- The biggest disadvantage of hash maps is that for smaller input sizes, they can be slower due to overhead. Because big O ignores constants, the $O(1)$ time complexity can sometimes be deceiving - it's usually something more like $O(10)$ because every key needs to go through the hash function.
- Hash tables can also take up more space. Dynamic arrays are actually fixed-size arrays that resize themselves when they go beyond their capacity. 

## 🔹 Pattern 1: Checking for existence

| Item               | Description |
|--------------------|-------------|
| **Core Idea**       | Determining if an element exists in $O(1)$.|
| **Strength**     | Since an array needs $O(n)$ to do this, using a shap map or set can improve the time complexity of an algorithm greatly, usually from $O(n^2)$ to $O(n)$.|
| **Typical Use Cases** | Two Sum, First Letter to Appear Twice|
| **Common Mistakes** |  |
| **Python Tips**     | Use `while` with `left<right` condition 
| **Sample Code**     |

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = {}
        for i in range(len(nums)):
            num = nums[i]
            complement = target - num
            if complement in dic: # This operation is O(1)!
                return [i, dic[complement]]
            
            dic[num] = i
        
        return [-1, -1]
```

### 🧠 Edge Cases & Mistakes
- Off-by-one errors
- Forgetting to reset state
- Overflow in sum calculations

### 💡 Tips
- Use `enumerate()` for index-value pairing in Python
- Watch out for constraints like "in-place"

### 🧪 Mistake Log

#### ❌ LeetCode 1207 - Unique Number of Occurrences
🔗  

**❌ Mistake:**  
Tried to check whether all elements in the list are unique by implementing for-loop through the list and comparing each element with the previous one. 

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

#### ❌ LeetCode 52 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.


## 🔹 Pattern 2: Counting

| Item               | Description |
|--------------------|-------------|
| **Core Idea**       | Tracking the frequency of things, which means our hash map will be mapping keys to integers.|
| **Strength**     | A hash map opens the door to solving problems where the constraint involves multiple elements.|
| **Typical Use Cases** | Two Sum, First Letter to Appear Twice|
| **Common Mistakes** |  |
| **Python Tips**     | Use `while` with `left<right` condition 
| **Sample Code**     |

```python
from collections import defaultdict

def find_longest_substring(s,k):
    counts = defaultdict(int)
    left = ans = 0 
    for right in range(len(s)):
        counts[s[right]] += 1
        while len(counts) > k:
            counts[s[left]] -= 1
            if counts[s[left]] == 0:
                del counts[s[left]]
            left += 1
        
        ans = max(ans, right - left +1)
    
    return ans
```

### 🧠 Edge Cases & Mistakes
- Off-by-one errors
- Forgetting to reset state
- Overflow in sum calculations

### 💡 Tips
- Use `enumerate()` for index-value pairing in Python
- Watch out for constraints like "in-place"

### 🧪 Mistake Log

#### ❌ LeetCode 1207 - Unique Number of Occurrences
🔗  

**❌ Mistake:**  
Tried to check whether all elements in the list are unique by implementing for-loop through the list and comparing each element with the previous one. 

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

#### ❌ LeetCode 52 - Maximum Subarray
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: `lyft_rides`, `lyft_drivers`

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.
