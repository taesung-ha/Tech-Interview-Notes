# Python Mistake Index (StrataScratch / Pandas)

A categorized list of Python mistakes made while solving StrataScratch problems using Pandas.

Click on each link to jump to the full explanation in `StrataScratch-Mistakes.md`.

---

## Merge / Join Mistakes

- Lyft Driver Wages – Used INNER JOIN instead of LEFT JOIN [(StrataScratch)](https://www.stratascratch.com/?via=signupnow&gad_source=1&gbraid=0AAAAA_CeujGTpJbwKfJvLlHyqRKxeS55b&gclid=CjwKCAjwn6LABhBSEiwAsNJrjpcjMuRtBp0l2wJGRVR4Pz5r8l3axl5GtDQWx-04MKIarole2Pm1WxoCKGkQAvD_BwE) [[Go to Mistake]](Python-Mistakes.md#1-problem-lyft-driver-wages)

  → Rows were dropped due to default join behavior.

---

## Date & Time Handling

- [Customer Revenue in March – Forgot how to convert 'YYYY-mm-dd' to 'YYYY-mm'](Python-Mistakes.md#4-problem-customer-revenue-in-march)  
  → Filtering didn’t work as expected due to string comparison.

---

## GroupBy & Aggregation

- [Total Transactions Per Customer – Forgot to reset index](Python-Mistakes.md#-problem-total-transactions-per-customer)  
  → Use `.dt.strftime('%Y-%m')` to convert the date format.

- [Top Percentile Fraud](Python-Mistakes.md#-11-top-percentile-fraud)  
  → Didn't know how to calculate the top 5 perentile of claims with the highest fraud scores. 

---

## Apply / Lambda Functions

- [Classify Business Type – Forgot how to structure multiple `else` conditions in `lambda` function](Python-Mistakes.md#3-problem-classify-business-type)  
  → `else` is used not only for other conditions, but also represent the 'remaining' or 'default' case.

---

## Sorting & Filtering

- [Order Details – Used `df['fisrt_name'] in list` instead of `df['first_name'].isin(list)`](https://platform.stratascratch.com/coding/9913-order-details?code_type=2 )  
  → used `in` incorrectly to compare multiple values.  
  [[Go to Mistake]](Python-Mistakes.md#1-problem-order-details)

- [Income By Title and Gender – use `df['column'].notna()` to identify not NAN values.](https://platform.stratascratch.com/coding/10077-income-by-title-and-gender?code_type=2)  
  → Whenever you want to filter not NAN value, use `df['column'].notna()`  
  [[Go to Mistake]](Python-Mistakes.md#1-income-by-title-and-gender)

- [Ranking Most Active Guests – Didn't know how to append rank column by python](https://platform.stratascratch.com/coding/10159-ranking-most-active-guests?code_type=2)  
  → Use `df['ranking'] = df['column'].rank(ascending=True, method = 'dense')` to add ranking columns to existing dataframe. 
  [[Go to Mistake]](Python-Mistakes.md#7-problem-ranking-most-active-guests)

---

## Data Processing
- [Apple Product Counts – forgot how to count distinct value for the column and how to fill 0 for the the null values](https://platform.stratascratch.com/coding/10141-apple-product-counts?code_type=2 )  
  → used `in` incorrectly to compare multiple values.  
  [[Go to Mistake]](Python-Mistakes.md#6-apple-product-counts)

- [Review of Categories – Didn't know how to split the columns based on the specific string](https://platform.stratascratch.com/coding/10049-reviews-of-categories?code_type=2)  
  → If a specific column contains multiple values concatenated together, use `df['column'].str.split(';')` to split them within each row. 
  [[Go to Mistake]](Python-Mistakes.md#9-review-of-categories)

---

## Regular Expression
- [Aromba-based Winery Search – Wasn't familiar with regular expression syntax](https://platform.stratascratch.com/coding/10026-find-all-wineries-which-produce-wines-by-possessing-aromas-of-plum-cherry-rose-or-hazelnut?code_type=2)  
  → Whenever you want to filter data that contains a specific string, use regular expressions.  
  [[Go to Mistake]](Python-Mistakes.md#8-Aroma-based-Winery-Search)

---

## Logical Issues

- [Max Number of K-Sum Pairs – Used multiple `if` conditions even though they are not mutually exclusive](Python-Mistakes.md#5-problem-Max-Number-of-K-sum-Pairs-Leetcode-1679)  
  → When using multiple `if` conditions, always be careful of whether the conditions are mutually exclusive.

- [Shortest Path in Binary Matrix – Forgot to include `[]` when using `set` or `deque`](Python-Mistakes.md#10-problem-shortest-path-in-binary-matrix)  
  → Whenever you need to continue adding value to the deque, wrap them in a list. 
---

## 🧠 Notes

- This is an index only — detailed explanations and code corrections live in `Python-Mistakes.md`.
- Add new links here whenever a new mistake is logged.
