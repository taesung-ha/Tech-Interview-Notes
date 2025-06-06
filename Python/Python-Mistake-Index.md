# ❌ Python Mistake Index (StrataScratch / Pandas)

A categorized list of Python mistakes made while solving StrataScratch problems using Pandas.

Click on each link to jump to the full explanation in `StrataScratch-Mistakes.md`.

---

## 🔗 Merge / Join Mistakes

- Lyft Driver Wages – Used INNER JOIN instead of LEFT JOIN [(StrataScratch)](https://www.stratascratch.com/?via=signupnow&gad_source=1&gbraid=0AAAAA_CeujGTpJbwKfJvLlHyqRKxeS55b&gclid=CjwKCAjwn6LABhBSEiwAsNJrjpcjMuRtBp0l2wJGRVR4Pz5r8l3axl5GtDQWx-04MKIarole2Pm1WxoCKGkQAvD_BwE) [[Go to Mistake]](python-mistakes.md#1-problem-lyft-driver-wages)

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

- [Top Ranked Songs – Used `sort_values()` instead of `nlargest()`](StrataScratch-Mistakes.md#🧪-problem-top-ranked-songs)  
  → Less efficient and potentially incorrect when dealing with duplicates.

---

## 🧠 Notes

- This is an index only — detailed explanations and code corrections live in `StrataScratch-Mistakes.md`.
- Add new links here whenever a new mistake is logged.
