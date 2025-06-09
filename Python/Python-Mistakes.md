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

## 🧪 [2] Problem: Income By Title and Gender
🔗 https://platform.stratascratch.com/coding/10077-income-by-title-and-gender?code_type=2  
📄 DataFrames: `sf_employee`, `sf_bonus`

**📌 Missed Function:**  
`df['column'].notna()` to identify not NAN values. 

**💡 Insight:**  
Whenever you want to filter not NAN value, use `df['column'].notna()`.

---

## 🧪 [3] Problem: Classify Business Type

🔗 https://platform.stratascratch.com/coding/9726-classify-business-type?code_type=2  
📄 DataFrames: `sf_restaurant_health_violations`

**❌ Mistake:**  
Forgot how to structure multiple `else` conditions in `lambda` function.

**✅ Fix:**  
Use multiple else branches in a lambda expression. 

```python
sf_restaurant_health_violations['business_name'].apply(
    lambda x: 'restaurant' if 'restaurant' in x.lower()
    else 'cafe' if 'cafe' in (x.lower()) or ('café' in x.lower()) or ('coffee' in x.lower())
    else 'school' if 'school' in x.lower()
    else 'other')
```

**📌 Missed Function:**  
(1) Multiple `else` can be used in `lambda` function (2) `x.lower()` is used to convert a word to lowercase. 

**💡 Insight:**  
`else` is used not only for other conditions, but also represent the 'remaining' or 'default' case.

---

## 🧪 [4] Problem: Customer Revenue in March

🔗 https://platform.stratascratch.com/coding/9782-customer-revenue-in-march?code_type=2   
📄 DataFrames: `orders`

**❌ Mistake:**  
Forgot how to convert 'YYYY-mm-dd' to 'YYYY-mm'. 

**✅ Fix:**  
Use `.dt.strftime('%Y-%m')` to convert the date format.

```python
orders['order_month'] = orders['order_date'].dt.strftime('%Y-%m')
```

---

## 🧪 [5] Problem: Max Number of K-Sum Pairs (Leetcode 1679)

🔗 https://leetcode.com/problems/max-number-of-k-sum-pairs/description/?envType=study-plan-v2&envId=leetcode-75  

**❌ Mistake:**  
Used multiple `if` conditions even though they are not mutually exclusive, so they ended up being triggered simultaneously. 

**✅ Fix:**  
Use `elif` instead of `if` or use multiple `if` conditions in a mutually exclusive way. 

```python
# Mistake
sorted_num = sorted(nums)
left = 0
right = len(nums)-1
ans = 0
while left < right:
    curr = sorted_num[left] + sorted_num[right]
    if curr == k:
        ans += 1
        left += 1
        right -= 1
    if curr > k:
        right -= 1
    if curr <= k:
        left += 1
#Fixed
sorted_num = sorted(nums)
        left = 0
        right = len(nums)-1
        ans = 0
        while left < right:
            curr = sorted_num[left] + sorted_num[right]
            if curr == k:
                ans += 1
                left += 1
                right -= 1
            elif curr > k:
                right -= 1
            elif curr < k:
                left += 1
        
        return ans
```

**💡 Insight:**  
When using multiple `if` conditions, always be careful of whether the conditions are mutually exclusive. Whenever possible, use elif in order to prevent logical errors. 
