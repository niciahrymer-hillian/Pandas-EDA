# 🧹 Pandas-EDA

### Data cleaning & exploratory data analysis in pandas — dedupe, fix types, handle nulls, standardize categories, tame outliers — in a live "dirty dataset" you clean step by step and watch the quality score climb.

![Chain Q](https://img.shields.io/badge/Chain%20Q-0891B2?style=for-the-badge) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge)](LICENSE-GPL) [![License: AGPL v3](https://img.shields.io/badge/License-AGPLv3-blue?style=for-the-badge)](LICENSE-AGPL)

[📖 Lesson Plan](docs/LESSON_PLAN.md) · [🎮 Interactive Tour](docs/interactive/index.html) · [🧾 Cheat Sheet](docs/CHEATSHEET.md)

<!-- SCREENSHOT PLACEHOLDER: docs/screenshots/clean.png -->

## Why This Was Built

"80% of the job is cleaning the data" is a cliché because it's true. Before any chart or model, real data
is duplicated, mistyped, full of nulls, and inconsistent (`NY`, `New York`, `new york` — same place, three
strings). This lesson makes cleaning **tactile**: a live table of deliberately messy records with the
exact pandas operation behind each fix — **dedupe, coerce dtypes, impute/drop nulls, standardize
categories, cap outliers** — and a **data-quality score** that climbs as you clean.

## Why This Matters (Industry Application)

Every analyst, data scientist, and data engineer spends most of their time here. Clean, correctly-typed,
consistent data is the prerequisite for trustworthy analysis — garbage in, garbage out. Knowing the
canonical pandas idioms (and *when* to drop vs impute) is day-one, everyday work.

## Topics Covered

| Area | pandas the lesson drills |
|------|--------------------------|
| Inspect | `df.info()`, `.describe()`, `.isna().sum()`, `.duplicated()` |
| Duplicates | `df.drop_duplicates(subset=…)` |
| Types | `pd.to_numeric(…, errors='coerce')`, `pd.to_datetime`, `astype` |
| Missing data | `.dropna()` vs `.fillna(mean/median/mode)`; when each is right |
| Categories | `.str.strip().str.lower()`, `.replace(mapping)`, `.map()` |
| Outliers | IQR rule, winsorize/cap vs drop |
| EDA | distributions, group-bys, correlations — after it's clean |

## How This Connects

Chain Q (Data Analytics). Feeds **SQL-For-Analytics** (same operations in SQL), **BI-Dashboards**
(clean data behind honest charts), and every modeling project in Chain R.

---
Dual licensed — [GPL v3](LICENSE-GPL) and [AGPL v3](LICENSE-AGPL).
