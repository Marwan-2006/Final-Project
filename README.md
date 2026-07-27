# Egypt-Energy

# Egypt's Energy Sector — Understanding the 2023 Electricity Crisis Through Data

A multi-tool data analytics project analyzing 20 years of Egyptian energy and economic data (2000–2023) to answer one question:

> Was the 2023 electricity crisis a generation shortfall, or something upstream?

The same panel data was analyzed five different ways — SQL Server, Python, Excel, Power BI, and Tableau — so the conclusion wouldn't rest on a single tool or a single chart.

---

## 📌 Project Overview

In the summer of 2023, Egypt experienced rolling power outages. This project tests the obvious assumption — that generation capacity ran out — directly against two decades of production, demand, gas-supply, and macroeconomic data.

**Conclusion:** It wasn't a generation shortage. Generation hit an all-time high in 2023 (221.9 TWh) and stayed above demand all year. The real strain was upstream, in the gas-supply chain — financial arrears, cut exports, and currency depreciation.

---

## 🗂️ Data Sources

The project workbook contains five linked sheets, all loaded into SQL Server with zero missing cells across the entire dataset:

| Sheet | Size | Key Columns |
|---|---|---|
| Annual Panel | 384 rows · 16 countries · 2000–2023 | population, GDP, electricity generation/demand, gas production, renewables share |
| Monthly Gas (Egypt) | 184 rows · 2011–2025 | exports/imports, indigenous production, arrears, EGP/USD rate, avg. temperature |
| Suez Canal Revenue | 22 rows | calendar/fiscal year, revenue (USD billion) |
| Zohr Gas Timeline | 20 rows | Zohr field output vs. national gas production |
| Electricity Tariffs | 77 rows | year, usage tier, price (EGP/kWh) |

Public reference sources for this class of data: World Bank Open Data, IEA, EIA, the Central Bank of Egypt, the Suez Canal Authority, and CAPMAS.

---

## 🛠️ Tools & Methods

### 1. SQL & Python
- Data cleaning: deduplication, date reconstruction, consistency checks
- Feature engineering: electricity gap, gas self-sufficiency, GDP per capita, trade balance, Zohr share
- 12 SQL Server queries, each paired with a chart
- A Random Forest Regressor predicting electricity demand from economic/demographic indicators only (excluding supply data), achieving **R² = 0.973** on a chronological train/test split (and 0.880 ± 0.130 under country-holdout cross-validation)
- 13 exploratory Python visualizations (pandas, matplotlib, seaborn, scikit-learn)

### 2. Excel
- Interactive workbook with pivot tables, slicers, and native charts
- KPI sheet with 18 calculated indicators
- Built-in electricity bill calculator

### 3. Power BI
- Three linked report pages: Overview, Egypt Trends, Country Comparison
- Country and year-range slicers driving every visual

### 4. Tableau
- Two dashboards: Natural Gas Analytics, and Electricity & Gas Performance
- Interactive year filters across dual-axis and KPI-card views

---

## 🔍 Key Insights

1. 2023 generation (221.9 TWh) was the highest on record — generation exceeded demand every year in the dataset.
2. The real problem was upstream: gas production peaked in 2021 (678 bcm), then declined, while arrears to foreign gas partners rose from ~$1.5B to over $5B.
3. Gas exports were cut 93.4% between summer 2022 and summer 2023 to redirect supply domestically.
4. The EGP's depreciation raised import costs in hard currency just as Suez Canal revenue fell (from $10.2B in 2023 to $4.2B in 2024).
5. Gas demand is strongly seasonal and temperature-driven — peak strain, weakest production, and highest arrears all land in the same months.
6. The Zohr field lifted national gas production by ~40% for several years, but its own output has been shrinking since ~2021.
7. A model using only economic and demographic indicators predicts electricity demand at R² = 0.973 — demand is structurally driven, not supply-driven.

---

## 📁 Repository Structure

```
├── data/               # Source workbook & cleaned datasets
├── sql/                # SQL Server queries
├── python/             # Data cleaning, EDA, and predictive model notebooks/scripts
├── excel/              # Interactive Excel dashboard
├── powerbi/            # Power BI report (.pbix)
├── tableau/            # Tableau workbook(s)
└── README.md
```

*(Adjust folder names above to match your actual repo layout.)*

---

## 🚀 Getting Started

1. Clone the repository
2. Load `data/Egypt_Energy_Project.xlsx` into SQL Server (or your preferred RDBMS)
3. Run the SQL scripts in `sql/` to reproduce the 12 core queries
4. Run the Python scripts/notebooks in `python/` for the exploratory charts and predictive model
5. Open the Excel, Power BI, or Tableau files directly to explore the dashboards

---

## 👥 Team

| Name | Tools |
|---|---|
| Arsany Fayez | Power BI, Tableau |
| Marwan Wael | Python, Tableau |
| Ramadan Mahmoud | SQL, Tableau |
| Omar Ibrahim | Excel, Tableau |
