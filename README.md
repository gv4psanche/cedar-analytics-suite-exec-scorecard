# Cedar Analytics Suite — Executive Scorecard Dashboard Solution

> A end-to-end business intelligence project: from company research and KPI design to data modeling and interactive dashboard prototyping aided by Claude Sonnet 4.6.

---

## Project Summary

This project delivers a full-stack analytics solution for **Cedar**, an intelligent IT asset lifecycle and disposition platform. Starting from raw company research, the work progresses through KPI framework design, data modeling, and the construction of five purpose-built BI dashboards — each targeting a distinct audience and business conversation.

The output is a ready-to-import data visualiztion solution (Power BI or Tableau): five CSV data sources, a fully interactive HTML mockup prototype, and this documentation.

---

### Executive Scorecard Dashboard 

<a href="https://gv4psanche.github.io/cedar-analytics-suite-exec-scorecard/">![Executive Scorecard Dashboard](images/Demo_WebPage.png)</a>

<a href="https://gv4psanche.github.io/cedar-analytics-suite-exec-scorecard/">Click To View Live Dashboard</a>
<br>
<br>

---

## About the Company

**Cedar** is an IT asset lifecycle platform serving large global enterprises across five verticals — financial services, technology & cloud, telecom & media, healthcare, and manufacturing. The company provides two families of service:

- **Lifecycle services** — deployment, staff augmentation, redeployment, and circularity programs
- **End-of-lifecycle services** — data center decommissioning, certified data destruction, and IT asset disposition (ITAD)

These services are unified under **ArcTrac**, Cedar's proprietary platform that gives enterprises real-time asset visibility, one-click ESG compliance reporting, and measurable financial value recovery across the full technology lifecycle.

**Published performance benchmarks used as KPI targets in this solution:**
- NPS score above **+70**
- Asset recovery rate **40%** above industry average via reuse-first methodology
- **60%** of the S&P 500 top 10 companies served

---

## KPI Framework

Fourteen KPIs were selected across four categories. The framework was designed to reflect Cedar's hybrid business model — part transactional ITAD services, part recurring platform (ArcTrac) — and to surface the most strategically important signal for a platform company: whether the installed base is expanding or contracting in value.

### Pipeline & Revenue

| KPI | Latest (Q2 2025) | Target |
|---|---|---|
| New ACV by vertical | $16.1M | — |
| ArcTrac platform attach rate | 47% | 60% by Q4 2025 |
| Services revenue mix | 62% lifecycle / 38% ITAD-only | — |
| Win rate vs. competitors | 91% | ≥ 85% |

### Customer Health

| KPI | Latest (Q2 2025) | Target |
|---|---|---|
| Net Revenue Retention (NRR) | 117% | ≥ 110% |
| NPS score | +71 | ≥ +70 |
| Time-to-value | 33 days | ≤ 30 days |
| S&P 500 top 10 logo count | 5 / 10 | — |

### Deal Quality & Efficiency

| KPI | Latest (Q2 2025) | Target |
|---|---|---|
| Average deal size | $429K | — |
| Average sales cycle | 91 days | — |
| Multi-service bundle rate | 47% | — |
| Demo-to-close conversion | 82% | ≥ 85% |

### ESG & Value Recovery

| KPI | Latest (Q2 2025) | Target |
|---|---|---|
| Asset circularity rate | 43% | ≥ 40% |
| Financial recovery returned to clients | $733K | — |

---

## Dashboard Architecture

Five dashboards were designed and prototyped. Each maps to a specific audience, a set of KPIs, and a recommended Power BI visual.

### 01 — Revenue & Pipeline
**Audience:** CRO, Sales leadership  
**Story:** Which verticals are driving new bookings? Is the services mix shifting from transactional ITAD toward recurring lifecycle contracts?  
**Key visuals:** Stacked bar + ArcTrac attach rate line overlay · Win/loss by competitor · Services mix donut · ACV trend line  
**Anomaly signal:** Any single vertical exceeding 45% of quarterly ACV = concentration risk

### 02 — Customer Health
**Audience:** Sales team, Customer success  
**Story:** Are customers happy and expanding? Who is at risk before renewal conversations begin?  
**Key visuals:** Dual-axis NRR + NPS line · Account health status table · Time-to-value bar · ARR treemap  
**Anomaly signal:** NPS and NRR softening in the same quarter = leading churn indicator (visible Q4 2024)

### 03 — Deal Quality & Efficiency
**Audience:** Sales ops, Sales reps  
**Story:** What does a good Cedar deal look like, and where is the process breaking down?  
**Key visuals:** Bubble scatter (deal size vs. cycle length, sized by bundle count) · Sales funnel · Cycle trend by vertical · Bundle rate combo  
**Anomaly signal:** Healthcare and Manufacturing in the bottom-right quadrant (long cycles, small deals) = ICP misalignment

### 04 — ESG & Value Recovery
**Audience:** Account managers, Sustainability leads  
**Story:** What financial and environmental value is Cedar returning to each client? Is the 40% circularity claim being met at the account level?  
**Key visuals:** Circularity rate vs. 40% benchmark combo · ESG report usage bar · Recovery value waterfall · Assets stacked area  
**Anomaly signal:** ESG report pull frequency below 1×/month = platform disengagement, predictive of churn 2–3 quarters out

### 05 — Executive Scorecard
**Audience:** CEO, Board, Executive team  
**Story:** Are we growing? Are customers happy? Is the platform gaining traction?  
**Key visuals:** NRR waterfall (new logo + expansion − churn − contraction) · KPI sparklines strip · ACV vs. pipeline line · Period-over-period delta table  
**Anomaly signal:** Expansion revenue approaching new logo revenue is a positive signal — Q2 2025 expansion ($4.9M) = 77% of new logo ($6.4M), indicating platform flywheel emerging

---

## Data Model

Five CSV files form a star-schema-style data model. All files cover **Q1 2024 – Q2 2025** (6 quarters).

```
01_revenue_pipeline.csv     → Revenue, ACV, win/loss, ArcTrac attach by vertical & quarter
02_customer_health.csv      → NRR, NPS, time-to-value, account status by account & quarter
03_deal_quality.csv         → Individual deal records: size, cycle length, bundle count
04_esg_value_recovery.csv   → Circularity rates, recovery value, CO₂ avoided by account
05_executive_scorecard.csv  → Aggregated quarterly summary of all 14 KPIs
```

**Relationship keys:**  
- All five tables join on `Quarter` + `Year` as the period key  
- Tables 02 and 04 also join on `Account_ID` for account-level slicing

**To load in Power BI:** Get Data → Text/CSV for each file. Set `Quarter` as text type and `Year` as whole number. Build a calculated date column for time intelligence and relate all tables through a shared Date dimension.

---

## Key Findings

Three structural shifts emerged across the six quarters of data:

1. **Platform is gaining traction.** ArcTrac attach rate grew from 24% → 47%. Deals with ArcTrac average $580K vs. $180K for ITAD-only — a 3.2× deal size premium.

2. **Healthcare is the breakout vertical.** ACV grew 260% over six quarters. Sales cycles fell from 130 → 98 days and bundle rates are rising — the clearest signal of improving ICP fit.

3. **Expansion revenue is approaching new logo.** In Q2 2025, expansion revenue ($4.9M) equals 77% of new logo ACV ($6.4M). When expansion exceeds new logo, Cedar crosses into platform flywheel territory.

**Risks flagged:**
- One account (Meridian Telecom) has sustained NRR at or below 103% for six quarters with no ArcTrac adoption — highest churn risk at Q3 2026 renewal
- Demo-to-close fell 2pp QoQ to 82% — the only KPI moving the wrong direction in Q2 2025

---

## Deliverables

| File | Description |
|---|---|
| `cedar_dashboard_mockup.html` | Interactive 5-view dashboard prototype (open in any browser) |
| `01_revenue_pipeline.csv` | Revenue & pipeline data source |
| `02_customer_health.csv` | Customer health data source |
| `03_deal_quality.csv` | Deal quality & efficiency data source |
| `04_esg_value_recovery.csv` | ESG & value recovery data source |
| `05_executive_scorecard.csv` | Executive scorecard data source |
| `cedar_analytics_overview.md` | This file |

---

## Tools & Stack

- **Research:** Public website analysis (dummy company by Claude  → cedar.com)
- **Data modeling:** Python / CSV — 6 quarters, 9 accounts, 14 KPIs
- **Prototyping:** HTML + Chart.js — interactive dashboard mockup
- **Production target:** Microsoft Power BI Desktop or Tableau Public/Desktop
- **Documentation:** Markdown

---

*Synthetic data only. All figures are illustrative, generated to reflect realistic business patterns based on publicly available company information. Replace with actual CRM, billing, and operational data before production use.*


