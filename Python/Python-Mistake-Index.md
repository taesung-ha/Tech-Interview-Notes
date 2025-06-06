# ❌ Python Mistake Index (StrataScratch / Pandas)

A categorized list of Python mistakes made while solving StrataScratch problems using Pandas.

Click on each link to jump to the full explanation in `StrataScratch-Mistakes.md`.

---

## 🔗 Merge / Join Mistakes

- Lyft Driver Wages – Used INNER JOIN instead of LEFT JOIN [(StrataScratch)](https://www.stratascratch.com/?via=signupnow&gad_source=1&gbraid=0AAAAA_CeujGTpJbwKfJvLlHyqRKxeS55b&gclid=CjwKCAjwn6LABhBSEiwAsNJrjpcjMuRtBp0l2wJGRVR4Pz5r8l3axl5GtDQWx-04MKIarole2Pm1WxoCKGkQAvD_BwE) [[Go to Mistake]](Python-Mistakes.md#1-problem-lyft-driver-wages)

  → Rows were dropped due to default join behavior.

---

## 📆 Date & Time Handling

- [User Retention – Forgot to convert string to datetime](StrataScratch-Mistakes.md#🧪-problem-user-retention)  
  → Filtering didn’t work as expected due to string comparison.

---

## 🧮 GroupBy & Aggregation

- [Total Transactions Per Customer – Forgot to reset index](StrataScratch-Mistakes.md#🧪-problem-total-transactions-per-customer)  
  → Result was a Series, not a DataFrame.

---

## 🔁 Apply / Lambda Functions

- [String Cleaning – Misused `lambda` inside `apply()`](StrataScratch-Mistakes.md#🧪-problem-string-cleaning)  
  → Mixed up `str.strip()` and `lambda x: x.strip()`.

---

## 📊 Sorting & Filtering

- [Order Details – Used `df['fisrt_name'] in list` instead of `df['first_name'].isin(list)`](https://platform.stratascratch.com/coding/9913-order-details?code_type=2 )  
  → used `in` incorrectly to compare multiple values.  
  [[Go to Mistake]](Python-Mistakes.md#1-problem-order-details)
---

## 🧠 Notes

- This is an index only — detailed explanations and code corrections live in `Python-Mistakes.md`.
- Add new links here whenever a new mistake is logged.
