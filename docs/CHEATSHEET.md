# 🧾 Pandas Cleaning & EDA — Key Objectives & Cheat Sheet

*The keep-forever, one-page reference.*

## Key objectives (what this project proves I can do)

- Triage a dataframe fast and list its problems.
- Dedupe on the **right key**; coerce types safely; handle nulls deliberately.
- Standardize messy categorical text.
- Detect + treat outliers with the IQR rule.
- Only then explore — group-bys, distributions, correlations you can trust.

## Inspect (always first)

```python
df.info()            # dtypes + non-null counts
df.describe()        # numeric summary — spot outliers/skew
df.isna().sum()      # nulls per column
df.duplicated().sum()
df["city"].value_counts()   # spot inconsistent categories
```

## Clean (in order)

```python
# 1) duplicates — choose the key
df = df.drop_duplicates(subset=["customer_id", "date"])

# 2) types — coerce junk to NaN (then CHECK how many)
before = df["spend"].isna().sum()
df["spend"] = pd.to_numeric(df["spend"], errors="coerce")
print(df["spend"].isna().sum() - before, "values coerced to NaN")

# 3) missing — drop vs impute
df = df.dropna(subset=["age"])              # if unusable / rare+random
df["age"] = df["age"].fillna(df["age"].median())   # if keeping rows (median = robust)

# 4) categories — standardize
df["city"] = (df["city"].str.strip().str.lower()
              .replace({"ny": "new york"}).str.title())

# 5) outliers — IQR rule
q1, q3 = df["spend"].quantile([.25, .75]); iqr = q3 - q1
lo, hi = q1 - 1.5*iqr, q3 + 1.5*iqr
df["spend"] = df["spend"].clip(lo, hi)      # winsorize (or filter to drop)
```

## Decision guide

| Situation | Do |
|---|---|
| Column skewed / has outliers | fill with **median**, not mean |
| 0 is a real value | never `fillna(0)` on that measure |
| Only one column matters | `dropna(subset=[col])`, not blanket `dropna()` |
| Extreme is a real signal | **don't** drop it — cap or investigate |
| Same thing, many spellings | standardize before any group-by |

## EDA (after it's clean)

```python
df.groupby("city")["spend"].agg(["mean", "median", "count"])
df["spend"].plot(kind="hist", bins=20)
df.corr(numeric_only=True)
```

## 30-second self-check

1. `errors="coerce"` → junk becomes **NaN** (check counts!).
2. Skewed fill → **median**.
3. Three spellings of one city → **standardize first**.
4. Outlier fence → **Q3 + 1.5·IQR**.
