# 📊 RappiPlus — Business Performance Analysis

### *From Revenue to Retention: a full-funnel view of what's driving results — and what's getting in the way*

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-pandasql-lightgrey?logo=sqlite&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Public-orange?logo=tableau&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Fer-Ramirez/rappiplus-business-performance-analysis/blob/main/rappiplus_business_performance_analysis.ipynb)

---

## 📊 Interactive Dashboard

The findings of this analysis are fully visualized in an interactive Tableau Public dashboard — covering revenue trends, product margins, conversion funnel, cohort retention, and A/B test results.

👉 [View Dashboard on Tableau Public](https://public.tableau.com/views/RappiPlusBusinessPerformanceAnalysis/Historia1)

---

## 🎯 Business Problem

RappiPlus is a subscription-based commerce platform operating across multiple Latin American markets. The business generates revenue at every stage of the customer journey — but revenue alone doesn't tell the full story.

This project answers four questions that matter for sustainable growth:

- Is the business actually profitable once costs are accounted for?
- Which channels and products are driving — or eroding — that profitability?
- Where in the funnel are users dropping off, and what does it cost?
- Are users coming back after their first purchase — or is growth entirely dependent on new acquisition?

---

## 💡 Key Findings

| Area | Finding |
|---|---|
| **Revenue & Profitability** | `$9.66M` total revenue at `30.5%` profit margin — sound fundamentals, but the model depends on transaction volume, not basket size (`1.5 units/order avg.) |
| **Marketing Efficiency** | All three channels deliver virtually identical ROAS: `3.49x`–`3.73x` — efficiency is confirmed, but incrementality is not |
| **Conversion Funnel** | `80%` overall conversion rate with a single critical failure point: `13.3%` of users abandon at Payment Info — every other stage loses under `5%` |
| **Cohort Retention** | `41–43%` weekly retention across all 5 cohorts and 4 weeks — stable engagement, but the `activo` flag does not confirm purchase events |
| **A/B Test** | Treatment converted at `16.29%` vs `15.69%` control — a `+3.80%` relative lift worth `~$92,800` per `10,000` users, though not statistically significant (p = `0.4161`) |

---

## 🧠 Analytical Approach

1. **Data Quality Audit** — Validated 3 datasets across structure, completeness, consistency, and numeric integrity before drawing any conclusions
2. **Profitability Analysis** — Decomposed revenue into COGS, gross profit, and net margin; cross-referenced with marketing spend to calculate ROAS by channel
3. **Funnel Analysis** — Built a 6-stage conversion funnel from platform event logs; quantified drop-off rates and revenue impact per stage
4. **Cohort Retention** — Tracked 5 monthly cohorts across 4 post-registration weeks using the platform's activity flag
5. **A/B Testing** — Applied a two-proportion Z-test to evaluate whether a redesigned checkout UI produced a statistically significant lift in conversion rate
6. **BI Dashboard** — Consolidated all findings into a 3-page Tableau Public dashboard structured as a narrative for executive stakeholders

---

## 🛠 Tools & Skills

- **Python** — pandas, numpy, matplotlib, seaborn, scipy
- **SQL** — pandasql (funnel construction, cohort segmentation, behavioral queries)
- **Tableau Public** — interactive dashboard with narrative structure (Overview → Products & Revenue → User Behavior)
- **Statistical Testing** — two-proportion Z-test, p-value interpretation, effect size framing
- **Business Communication** — findings translated into actionable implications with revenue estimates

---

## 📁 Project Structure

```
rappiplus-business-performance-analysis/
│
├── rappiplus_business_performance_analysis.ipynb   # Main analysis notebook
│
├── datasets/
│   ├── orders_clean.csv
│   ├── catalog_clean.csv
│   ├── marketing_clean.csv
│   ├── orders_master.csv          # Flat file for Tableau (no joins)
│   ├── funnel_stages.csv
│   ├── funnel_by_channel.csv
│   ├── cohort_retention.csv
│   ├── ab_test_results.csv
│   └── roas_by_channel.csv
│
└── README.md
```

---

## ▶️ How to Run

### Option 1: Google Colab (Recommended)

1. Click the **Open in Colab** badge at the top of this page
2. Upload the datasets from the `datasets/` folder in this repo
3. Run all cells sequentially

### Option 2: Local Environment

```bash
git clone https://github.com/Fer-Ramirez/rappiplus-business-performance-analysis
cd rappiplus-business-performance-analysis
pip install pandas numpy matplotlib seaborn scipy pandasql
jupyter notebook
```

> **Note:** The notebook loads datasets from local paths. Ensure all files in `datasets/` are present in the working directory before running.

---

## ⚠️ Data Quality & Limitations

- **Profit figures are directional, not audited.** An inconsistency between unit prices in orders and unit costs in the catalog was flagged during cleaning. Margin figures reflect the analytical model and should not be used for financial reporting without a governance review.
- **Cohort retention measures engagement, not conversion.** The `activo` flag records platform activity — not confirmed purchases. The `41–43%` weekly retention rate cannot be directly equated with revenue-generating return visits.
- **The A/B test was underpowered.** p = `0.4161` does not confirm the redesign had no effect — it confirms the experiment lacked the statistical power to detect the observed lift reliably.
- **5-month observation window.** No seasonality analysis or year-over-year comparison is possible with the current data coverage.

---

## 🎯 Final Takeaway

RappiPlus has a profitable business, a high-intent user base, and stable weekly engagement. The analysis consistently points to one unresolved tension: a revenue model dependent on transaction frequency, interrupted by a single, bounded friction point that `13.3%` of ready-to-buy users don't clear.

**Fixing payment friction is the clearest, highest-confidence lever available — and the data makes the case for it from three independent angles: funnel drop-off, cohort behavior, and the A/B test.**
