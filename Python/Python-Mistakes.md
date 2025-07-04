# Python Mistakes 

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

---

## 🧪 [6] Problem: Apple Product Counts

🔗 https://platform.stratascratch.com/coding/10141-apple-product-counts?code_type=2

**❌ Mistake:**  
forgot how to count distinct value for the column and how to fill 0 for the the null values instead of the blank.

**✅ Fix:**  
- Use `df.groupby['column1'][''column2'].nunique()` to count distinct value.
- Use `df.fillna(0)` to fill null values.

```python
apple_language = apple_df.groupby('language')['user_id'].nuique().reset_index()
total['n_apple_users'] = total['n_apple_users'].fillna(0)
```

**💡 Insight:**  
- Whenever you count the distinct value for the column, don't forget `df['column'].nuinque()`
- To fill null values with 0, use `df['column1'].fillna(0)`

---

## 🧪 [7] Problem: Ranking Most Active Guests

🔗 https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=2
📄 DataFrames: `airbnb_contacts`

**📌 Missed Function:**  
Didn't know how to append rank column by python.

**✅ Fix:**  
Use `df['ranking'] = df['column'].rank(ascending=True, method = 'dense')` to add ranking columns to existing dataframe.

```python
df_groupby['ranking'] = df_groupby['n_messages'].rank(ascending=False, method='dense')
```

---

## 🧪 [8] Problem: Aroma-based Winery Search

🔗 https://platform.stratascratch.com/coding/10026-find-all-wineries-which-produce-wines-by-possessing-aromas-of-plum-cherry-rose-or-hazelnut?code_type=1  
📄 DataFrames: `winemag_p1`

**📌 Missed Function:**  
wasn't familiar with regular expression in Python

**✅ Fix:**  
Use Regular expression to filter the data that contains a specific string.

```python
aromas = ['plum', 'cherry', 'rose', 'hazelnut']
patterns = r'\b(?:' + ''.join(aromas) + r')\b'
winemag_p1[winemag_p1['description'].str.contains(patterns, case=False, regex=True)]
```

---

## 🧪 [9] Problem: Review of Categories

🔗  https://platform.stratascratch.com/coding/10049-reviews-of-categories?code_type=2  

**❌ Mistake:**  
Didn't know how to split the columns based on the specific string. 


**✅ Fix:**  
Use `df['column'].str.split(';')`

```python
yelp_business['categories'] = yelp_business['categories'].str.split(';')
df = yelp_business.explode('categories')
df.groupby('categories')['review_count'].sum().reset_index().sort_values(by='review_count', ascending=False)
```

**💡 Insight:**  
- If a specific column contains multiple values concatenated together, use `df['column'].str.split(';')` to split them within each row.

---

## 🧪 [10] Problem: Shortest Path in Binary Matrix

🔗 https://leetcode.com/problems/shortest-path-in-binary-matrix/description/ 

**❌ Mistake:**  
Forgot to include `[]` when using `set` or `deque`. 

**✅ Fix:**  
Include `[]` because a list needs to be passed into deque. 

```python
from collections import deque

class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        if grid[0][0] == 1:
            return -1
        
        def valid(row, col):
            return 0 <= row < n and 0 <= col < n and grid[row][col] == 0
        
        n = len(grid)
        seen = {(0, 0)}
        queue = deque([(0, 0, 1)]) # row, col, steps
        directions = [(0, 1), (1, 0), (1, 1), (-1, -1), (-1, 1), (1, -1), (0, -1), (-1, 0)]
        
        while queue:
            row, col, steps = queue.popleft()
            if (row, col) == (n - 1, n - 1):
                return steps
            
            for dx, dy in directions:
                next_row, next_col = row + dy, col + dx
                if valid(next_row, next_col) and (next_row, next_col) not in seen:
                    seen.add((next_row, next_col))
                    queue.append((next_row, next_col, steps + 1))
        
        return -1
```

**💡 Insight:**  
- Whenever you need to continue adding value to the deque, wrap them in a list. 

---

## 🧪 [11] Problem: Top Percentile Fraud

🔗 https://platform.stratascratch.com/coding/10303-top-percentile-fraud?code_type=2

**❌ Mistake:**  
Didn't know how to calculate the top 5 perentile of claims with the highest fraud scores. 

**✅ Fix:**  
Use `df.groupby['group']['column'].percentile(0.95)`

```python
import pandas as pd

# Start writing code
thresholds = fraud_score.groupby('state')['fraud_score'].quantile(0.95).reset_index()
thresholds.columns = ['state', 'threshold']

df_with_thresholds = pd.merge(fraud_score, thresholds, how='left', on='state')
df_with_thresholds[df_with_thresholds['fraud_score'] >= df_with_thresholds['threshold']].drop(columns='threshold')
```

**💡 Insight:**  
- To calculate the percentile for some column within group, use `percentile_cont(0.95) within group (order by)`.

---

## 🧪 [12] Problem: Election Results

🔗 https://platform.stratascratch.com/coding/2099-election-results?code_type=2  

**❌ Mistake:**  
Forgot how to remove rows with null values. 

**✅ Fix:**  
Use `df.dropna()`

```python
import pandas as pd

voting_results = voting_results.dropna()
voter_counts = voting_results.groupby('voter')['candidate'].count().reset_index()
merge = pd.merge(voting_results, voter_counts, how='left', left_on='voter', right_on='voter')
merge['candidate_y'] = merge['candidate_y'].apply(lambda x: 1/x if x!=0 else 0)
merge.columns = ['voter', 'candidate', 'weighted_vote']
merge.sort_values(by='candidate')
weighted_candidate = merge.groupby('candidate')['weighted_vote'].sum().reset_index().sort_values(by='weighted_vote', ascending=False)
weighted_candidate['candidate'].head(1)
```

---

## 🧪 [14] Problem: Processed Ticket Rate By Type

🔗 https://platform.stratascratch.com/coding/9781-find-the-rate-of-processed-tickets-for-each-type?code_type=2
📄 Table: `facebook_complaints`

**❌ Mistake:**  
Didn't realize to apply multiple aggregation functions at once using the `agg` method with the `groupby` function. 

**✅ Fix:**  
Use `df.groupby(['column']).agg({'column1':'sum', 'column2':'count'})` 

```python
import pandas as pd
facebook_complaints['processed'] = facebook_complaints['processed'].astype(int)
grouped = facebook_complaints.groupby(['type']).agg({'processed':'sum', 'complaint_id':'count'}).reset_index()
grouped['processed_rate'] = (grouped['processed'] / grouped['complaint_id']).round(2)
grouped[['type', 'processed_rate']]
```
**📌 Missed Concept:**
- `cast(sum(spam) as float)`

**💡 Insight:**  
In Python, you don't have to use multiple groupby calculation separately. Just use `df.groupby(['column']).agg({'column1':'sum', 'column2':'count'})`

---

## 🧪 [15] Problem: Best Selling Item

🔗 https://platform.stratascratch.com/coding/10172-best-selling-item?code_type=2  
📄 Table: `online_retail`

**❌ Mistake:**  
Didn't realize to apply multiple merge `on` conditions. 

**✅ Fix:**  
Use `pd.merge(df1, df2, how='in', on=['column1', 'column2'])`
```python
import pandas as pd

online_retail['month'] = online_retail['invoicedate'].dt.strftime('%m')
online_retail['total_paid'] = online_retail['quantity'] * online_retail['unitprice']
groupby = online_retail.groupby('month')['total_paid'].max().reset_index()
preprocessing = online_retail.groupby(['description', 'month'])['total_paid'].sum().reset_index()
groupby_preprocessing = preprocessing.groupby('month')['total_paid'].max().reset_index()
ans = pd.merge(groupby_preprocessing, preprocessing, how='left', on=['month', 'total_paid'])
ans[['month', 'description', 'total_paid']]
```

**💡 Insight:**  
In Python, if you don't apply multiple on conditions in merge, you could not merge the datasets correclty. 

---

## 🧪 [16] Problem: Top 10 Songs 2010

🔗 https://platform.stratascratch.com/coding/9650-find-the-top-10-ranked-songs-in-2010?code_type=2
📄 Table: `billboard_top_100_year_end`

**❌ Mistake:**  
Didn't know how to delete duplicate data based on a specific column. 

**✅ Fix:**  
Use `df.drop_dupliates(subset='column_name')`
```python
import pandas as pd

top_100_2010 = billboard_top_100_year_end[billboard_top_100_year_end['year'] == 2010]
top_100_2010 = top_100_2010[['group_name', 'song_name']]
top_100_2010 = top_100_2010.drop_duplicates(subset='song_name')
top_100_2010['rank'] = range(1, len(top_100_2010)+1)
top_100_2010.head(10)
```
