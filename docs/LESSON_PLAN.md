# 📖 Lesson Plan — Pandas-EDA

> **Chain Q — Data Analytics** | Data cleaning + EDA — taught on a live dirty dataset you clean step by step.

## What This Project Is

A self-contained lesson on cleaning messy data and doing exploratory data analysis in pandas. The
[interactive tour](interactive/index.html) is a **live dirty dataset**: a table of deliberately messy
records with the exact pandas operation behind each fix, and a **data-quality score** that rises as you
dedupe, coerce types, handle nulls, standardize categories, and cap outliers.

## Learning Objectives

By the end I can:

1. Inspect a dataframe fast (`info`, `describe`, `isna().sum()`, `duplicated()`).
2. Remove duplicates on the right key (`drop_duplicates(subset=…)`).
3. Coerce types safely (`to_numeric(errors='coerce')`, `to_datetime`, `astype`).
4. Choose **drop vs impute** for missing data and justify it.
5. Standardize categorical text (`str.strip().str.lower()`, `replace`, `map`).
6. Detect and handle **outliers** (IQR rule; cap vs drop).
7. Explore the cleaned data (distributions, group-bys, correlations).

## Software You Will Use

- Python + pandas (+ Jupyter for the real exercises — a companion notebook mirrors the tour steps).
- The interactive tour (browser only) for the guided walkthrough.

## Build Order

1. Inspect the dirty dataset; list its problems.
2. Dedupe → fix types → handle nulls → standardize categories → cap outliers, watching the quality score.
3. Do a quick EDA pass (group-by, a distribution) on the clean data.
4. Take the quiz; keep the cheat sheet.

## Common Mistakes to Avoid

- `fillna(0)` on a measure where 0 is a real value (skews the mean) — pick mean/median/mode deliberately.
- Dropping rows with any null (`dropna()`) when you only needed one column.
- Deduping on the whole row when the real key is `customer_id + date`.
- Silent type coercion that turns bad values into `NaN` you never notice — always check counts before/after.

## Check Your Understanding

The interactive tour ends with a quiz (Standard #7): drop vs impute, dedupe keys, `errors='coerce'`,
and the IQR outlier rule.

## Why This Matters (Industry Application)

Cleaning is the majority of real analytics/DS work. The person who cleans correctly — and knows *why* a
choice (impute vs drop) is right — produces analysis others can trust.

## Reflection Questions

- When is `median` a better fill than `mean`?
- Why can `errors='coerce'` be dangerous, and how do you guard against it?
- Give a case where dropping outliers is wrong.
