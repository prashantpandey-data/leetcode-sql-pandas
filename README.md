# 📊 Data Analyst Prep | LeetCode SQL & Pandas

SQL and Pandas solutions focused on real analyst work: filtering, joins, aggregation, window functions, retention and cohort-style analysis. Every solution comes with the approach, edge cases, and the **business question** it answers.

🔗 **LeetCode Profile:** [leetcode.com/u/prashantpandey-data](https://leetcode.com/u/prashantpandey-data/)

---

## 🎯 Goal

Become interview-ready for Data Analyst roles by mastering SQL and Pandas, and by learning to translate a business question into a query.

## 📈 Progress

| Track | Solved |
|-------|--------|
| SQL 50 | XX / 50 |
| 30 Days of Pandas | XX / 30 |
| Advanced SQL (window functions, self-joins) | XX |

> Updated regularly. Last update: November 2026

---

## 🧠 Skills Covered

| Skill | Example Problems | Business Use |
|-------|------------------|--------------|
| Filtering and basic SELECT | 1757, 584, 595, 1148, 1683, 620 | Segmenting records, finding invalid or qualifying entries |
| Joins (INNER / LEFT / CROSS) | 1068, 1378, 1581, 1280, 577 | Finding missing data, customers vs transactions |
| Self-joins | 197, 1731, 570, 180 | Comparing a row with a previous day, manager-report hierarchies |
| Aggregation + HAVING | 1327, 596, 1045, 1075, 1729, 2356 | Thresholds, top performers, unique counts |
| Conditional aggregation (CASE) | 1193, 1907, 1934, 1211, 1633 | Approval rate, conversion rate, segmentation |
| Window functions | 185, 1204, 1321, 1070, 1164 | Ranking, running totals, moving averages, latest value per group |
| Retention / cohort | 550, 1174, 1141 | Day-1 retention, first-order behaviour, daily active users |
| String and regex | 1517, 1527, 1667, 1484 | Cleaning and validating text fields |
| Date logic | 1141, 1164, 1327 | Date windows, month-wise reporting |
| Pandas basics | 2877, 2878, 2879, 2880, 2881 | DataFrame creation, selection, new columns |
| Pandas cleaning | 2882, 2883, 2884, 2885, 2886, 2887 | Duplicates, missing values, renaming, type changes |
| Pandas reshaping | 2888, 2889, 2890, 2891 | Concatenate, pivot, melt, method chaining |

---

## 💡 Featured Solutions

### Confirmation Rate (1934)
**Business question:** What percentage of users completed their confirmation?
**Approach:** `LEFT JOIN` + `AVG(CASE WHEN action = 'confirmed' THEN 1 ELSE 0 END)`, so users who never made a request still show up with a rate of 0.
**Insight:** A low rate points to drop-off in the onboarding or verification flow.

### Immediate Food Delivery II (1174)
**Business question:** Of every customer's first order, how many were delivered the same day they wanted?
**Approach:** Find each customer's first order date with `MIN(order_date)`, then average an "is immediate" flag over just those rows.
**Insight:** First-order experience strongly drives repeat purchase, so this is a key retention metric.

### Game Play Analysis IV (550)
**Business question:** What fraction of players come back the day after they first log in?
**Approach:** Derive each player's first login date, join back on `first_login + 1 day`, and divide by total players.
**Insight:** Classic Day-1 retention, used in almost every product analytics team.

### Department Top Three Salaries (185)
**Business question:** Who are the top earners in each department?
**Approach:** `DENSE_RANK() OVER (PARTITION BY departmentId ORDER BY salary DESC)` and keep rank <= 3. `DENSE_RANK` is used so tied salaries are not dropped.

### Restaurant Growth (1321)
**Business question:** How is revenue trending on a 7-day moving basis?
**Approach:** Aggregate to one row per day first, then apply a window of `ROWS BETWEEN 6 PRECEDING AND CURRENT ROW`.

---

## ⚠️ Mistakes I Learned From

- **NULL handling:** `referee_id <> 2` silently drops NULL rows (584). Always add `OR col IS NULL` when NULLs should be kept.
- **LEFT JOIN + WHERE:** Putting a filter on the right table in `WHERE` turns a `LEFT JOIN` into an inner join. Keep it in `ON` (1251).
- **COUNT(*) vs COUNT(col):** `COUNT(*)` counts unmatched rows as 1, `COUNT(col)` ignores NULLs (1280).
- **RANK vs DENSE_RANK vs ROW_NUMBER:** Ties behave differently, and the wrong choice gives wrong top-N results (185, 1070).
- **Missing categories:** `GROUP BY` drops categories with no rows. Use `UNION ALL` of aggregates to guarantee all of them appear (1907).
- **Pandas operators:** Use `|` and `&` with parentheses around each condition, not `or` / `and` (595).

---

## 📂 Repository Structure

```text
LeetCode/
├── SQL/
│   ├── filtering/
│   ├── joins/
│   ├── aggregation/
│   ├── window_functions/
│   └── retention/
├── Pandas/
│   ├── basics/
│   ├── cleaning/
│   └── reshaping/
├── notes.md
└── README.md
```

Each solution file contains:
- Problem number and name
- Approach in a few lines
- Time / space complexity (where relevant)
- The code, plus an alternative approach when there is one

---

## 🚀 Next Steps

- [ ] Finish SQL 50 and 30 Days of Pandas
- [ ] Practise Medium and Hard SQL (window functions, recursive CTEs)
- [ ] Build a small end-to-end project on a public dataset (Kaggle) with 5-6 business questions answered in SQL
- [ ] Build one dashboard (Power BI / Tableau / Excel) and add screenshots here

---

## 🛠 Tools

MySQL · Python (Pandas) · LeetCode · Git / GitHub

---

## 📬 Contact

- LinkedIn: https://www.linkedin.com/in/prashant-pandey-39694b3b0
- LeetCode: [prashantpandey-data](https://leetcode.com/u/prashantpandey-data/)
