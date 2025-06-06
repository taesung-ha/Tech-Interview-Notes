# ❌ StrataScratch Mistakes (Python)

This is a growing log of mistakes I made while solving StrataScratch problems using Pandas.  
Each entry includes the error, correct fix, missed function, and a key takeaway.

---

## 🧪 [1] Problem: Lyft Driver Wages  
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: lyft_rides, lyft_drivers

**❌ Mistake:**  
Used `pd.merge()` without specifying `how`, resulting in an inner join that excluded drivers without matched rows.

**✅ Fix:**  
Use `how="left"` in `pd.merge()` to retain all left-hand entries.

```python
# ❌ Incorrect
pd.merge(drivers, wages, on="driver_id")

# ✅ Correct
pd.merge(drivers, wages, on="driver_id", how="left")
```
### 📌 Missed Function:
`pd.merge()` Combines two DataFrames. Default `how='inner'` may drop rows.
Set `how='left'` to preserve all from the left.

### 💡 Insight:
Never assume the default behavior of joins. Always write how= explicitly.

---

## 🧪 [2] Problem: User Retention
🔗 https://platform.stratascratch.com/coding/10308/lyft-driver-wages  
📄 Tables: lyft_rides, lyft_drivers

**❌ Mistake:**
Filtered string-formatted dates without converting to datetime → comparison silently failed.

**✅ Fix:**
Convert to datetime before comparing.

```python
# ❌ Wrong
df[df['event_date'] >= "2022-01-01"]

# ✅ Correct
df['event_date'] = pd.to_datetime(df['event_date'])
df[df['event_date'] >= "2022-01-01"]
```

### 📌 Missed Function:
`pd.to_datetime(column)`
Converts strings to datetime64 objects for filtering, plotting, and time-based operations.

### 💡 Insight:
Always confirm the data type before filtering dates. Use df.dtypes.