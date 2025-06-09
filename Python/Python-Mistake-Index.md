# ❌ Python Mistake Index (StrataScratch / Pandas)

A categorized list of Python mistakes made while solving StrataScratch problems using Pandas.

Click on each link to jump to the full explanation in `StrataScratch-Mistakes.md`.

---

## 🔗 Merge / Join Mistakes

- Lyft Driver Wages – Used INNER JOIN instead of LEFT JOIN [(StrataScratch)](https://www.stratascratch.com/?via=signupnow&gad_source=1&gbraid=0AAAAA_CeujGTpJbwKfJvLlHyqRKxeS55b&gclid=CjwKCAjwn6LABhBSEiwAsNJrjpcjMuRtBp0l2wJGRVR4Pz5r8l3axl5GtDQWx-04MKIarole2Pm1WxoCKGkQAvD_BwE) [[Go to Mistake]](Python-Mistakes.md#1-problem-lyft-driver-wages)

  → Rows were dropped due to default join behavior.

---

## 📆 Date & Time Handling

- [Customer Revenue in March – Forgot how to convert 'YYYY-mm-dd' to 'YYYY-mm'](Python-Mistakes.md#4-problem-customer-revenue-in-march)  
  → Filtering didn’t work as expected due to string comparison.

---

## 🧮 GroupBy & Aggregation

- [Total Transactions Per Customer – Forgot to reset index](Python-Mistakes.md#-problem-total-transactions-per-customer)  
  → Use `.dt.strftime('%Y-%m')` to convert the date format.

---

## 🔁 Apply / Lambda Functions

- [Classify Business Type – Forgot how to structure multiple `else` conditions in `lambda` function](Python-Mistakes.md#3-problem-classify-business-type)  
  → `else` is used not only for other conditions, but also represent the 'remaining' or 'default' case.

---

## 📊 Sorting & Filtering

- [Order Details – Used `df['fisrt_name'] in list` instead of `df['first_name'].isin(list)`](https://platform.stratascratch.com/coding/9913-order-details?code_type=2 )  
  → used `in` incorrectly to compare multiple values.  
  [[Go to Mistake]](Python-Mistakes.md#1-problem-order-details)

- [Income By Title and Gender – use `df['column'].notna()` to identify not NAN values.](https://platform.stratascratch.com/coding/10077-income-by-title-and-gender?code_type=2)  
  → Whenever you want to filter not NAN value, use `df['column'].notna()`  
  [[Go to Mistake]](Python-Mistakes.md#1-income-by-title-and-gender)
---

## 🧠 Notes

- This is an index only — detailed explanations and code corrections live in `Python-Mistakes.md`.
- Add new links here whenever a new mistake is logged.
