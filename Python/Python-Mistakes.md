# ❌ Python Mistakes 

This is a growing log of mistakes I made while solving StrataScratch problems using Pandas.  
Each entry includes the error, correct fix, missed function, and a key takeaway.

---

## 🧪 [1] Problem: Order Details
🔗 https://platform.stratascratch.com/coding/9913-order-details?code_type=2  
📄 DataFrames: `customers`, `orders`

**❌ Mistake:**  
used `df_merge['first_name] in ['Jill', 'Eva']`. instead  of `df.isin(['Jill', 'Eva'])`.

**✅ Fix:**  
Use `df.isin(['Jill', 'Eva'])`

```python
# ❌ Incorrect
df_merge[df_merge['first_name'] in ['Jill', 'Eva']]

# ✅ Correct
df_merge[df_merge['first_name'].isin(['Jill', 'Eva'])]
```

**📌 Missed Function:**  
`==` compares only a single value, whereas `df.isin()` can compare against multiple values at once, such as a list, series, or set. 

**💡 Insight:**  
Whenever you compare multiple values, use `df.isin()`.

---

## 🧪 [1] Problem: Order Details
🔗 https://platform.stratascratch.com/coding/9913-order-details?code_type=2  
📄 DataFrames: `customers`, `orders`

**❌ Mistake:**  
used `df_merge['first_name] in ['Jill', 'Eva']`. instead  of `df.isin(['Jill', 'Eva'])`.

**✅ Fix:**  
Use `df.isin(['Jill', 'Eva'])`

```python
# ❌ Incorrect
df_merge[df_merge['first_name'] in ['Jill', 'Eva']]

# ✅ Correct
df_merge[df_merge['first_name'].isin(['Jill', 'Eva'])]
```

**📌 Missed Function:**  
`==` compares only a single value, whereas `df.isin()` can compare against multiple values at once, such as a list, series, or set. 

**💡 Insight:**  
Whenever you compare multiple values, use `df.isin()`.

---
