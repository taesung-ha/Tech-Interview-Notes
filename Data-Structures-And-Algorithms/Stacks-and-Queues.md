# 📘 Stacks

## ✅ Summary
- Stacks are useful for string matching because it saves a "history" of the previous characters. 
- Another term used to describe stacks is **LIFO**, which stands for **last in, first out**. The last (most recent) element placed inside is the first element to come out. 
- $O(1)$ push, pop, and random access, and $O(n)$ search. 

## 🔹 Pattern 1: Valid Parenthesis

| Item               | Description |
|--------------------|-------------|
| **Core Idea**       | Leverage the power of stacks; **Last in, First Out (LIFO)** - the last opening bracket we saw is the first one we should close, which is perfect functionality for a stack to provide. |
| **Strength**     | Because the stack's push and pop operations are $O(1)$, this gives us a time complexity of $O(n)$, where $n$ is the size of the input array. |
| **Python Tips**     | Use a hasp map to map each opening bracket to its closing bracket.  
| **Sample Code**     |

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        matching = {"(": ")", "[": "]", "{": "}"}
        
        for c in s:
            if c in matching: # if c is an opening bracket
                stack.append(c)
            else:
                if not stack:
                    return False
                
                previous_opening = stack.pop()
                if matching[previous_opening] != c:
                    return False
 
        return not stack
```

### 🧠 Edge Cases & Mistakes


### 💡 Tips


### 🧪 Mistake Log

#### ❌ LeetCode 

**❌ Mistake:**  

**✅ Fix:**  

```python
```
**📌 Missed Function:**  

**💡 Insight:**  

---

