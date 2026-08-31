#  Global COVID-19  Surveillance  and metrics Dashboard

An enterprise-ready BI surveillance dashboard built with **Apache Superset**, **PostgreSQL**, and **Docker Desktop**. This dashboard aggregates global infection statistics, tracks active disease burden, and highlights key geographical hot spots.

---

## 📊 Executive Summary & Metrics Key

| Metric | Description |
| :--- | :--- |
| **Global Cumulative Confirmed** | Total positive cases reported worldwide since tracking inception. |
| **Total Global Mortality** | Total worldwide deceased cases linked to COVID-19. |
| **Active Cases** | Estimated currently infected individuals requiring active monitoring or healthcare support. |


---

##  Dataset Architecture (`public.covid19_daily`)

The underlying datasource is built on daily aggregated global COVID-19 records.

### Schema Breakdown
- **`ObservationDate` / `Date`** *(DATE)*: Daily tracking timestamp.
- **`Country/Region`** *(VARCHAR)*: Country or reporting territorial entity.
- **`Province/State`** *(VARCHAR)*: Sub-national administrative region (where available).
- **`Confirmed`** *(INTEGER)*: Cumulative positive cases reported.
- **`Deaths`** *(INTEGER)*: Cumulative fatalities reported.
- **`Recovered`** *(INTEGER)*: Cumulative recovered cases reported.

###  Data Integrity & Anomaly Handling
- **Reporting Discontinuation:** Global tracking of **Recovered Cases** by major public health entities (e.g., Johns Hopkins CSSE) was officially discontinued in mid-2021 due to changes in municipal health reporting standards.
- **Null Handling Strategy:** To prevent calculation errors (`NaN` or `No data` displays), custom SQL metrics utilize `COALESCE(field, 0)` to maintain metric calculations across incomplete date ranges.

---

## 🛠️ Dashboard Architecture & Visualizations

1. **Executive KPI Header:** High-level single-value callouts for Global Confirmed ($677\text{M}$), Active Cases ($670\text{M}$), and Total Deaths ($6.88\text{M}$).
2. **Top 10 Most Affected Countries:** Horizontal bar visual ranking countries by cumulative case totals to identify high-impact geographical zones.
3. **Time-Series Analysis:** Line visual tracking global case progression over time.

---

