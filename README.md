<div align="right">

**English** | [العربية](README.ar.md)

</div>

# Saudi Labor Market Transformation Dashboard (2021–2026)

An end-to-end **Power BI** analytics project tracking the structural evolution of the **Saudi Labor Market from Q1 2021 to Q2 2026** and evaluating national progress against **Saudi Vision 2030** targets.

---

## Business Objectives

This dashboard is designed for both general audiences and executive stakeholders to answer two core questions:
1. **Market Evolution:** How have employment levels, wages, regional participation, and workforce demographics evolved between 2021 and 2026?
2. **Vision 2030 Progress:** How close is the Kingdom to achieving its strategic localization, unemployment, and female empowerment targets?

---

## Key Executive Findings (Q1 2021 – Q2 2026)

| Pillar | Headline Metric | Strategic Insight |
| :--- | :---: | :--- |
| **Saudi Unemployment** | **`6.50%`** | Declined from **12.17%** (Q1 2021) to **6.50%** (Q2 2026), surpassing the Vision 2030 target of **7%** ahead of schedule. Overall Kingdom unemployment dropped from **5.8%** to **3.0%**. |
| **Workforce & Private Sector** | **`14.0M`** | Total workforce reached **14.0M** (+8.7% YoY), with Saudi workers growing from **2.1M** to **3.2M**. Saudi employment shifted toward the private sector (**50.1%**), overtaking the public sector (**49.0%**). |
| **Female Participation & Regions** | **`33.70%`** | Saudi female labor participation rose from **31.90%** to **33.70%**, progressing toward the revised **40%** 2030 target. Participation is highest in the Eastern Province (**71.2%**) and Riyadh (**70.5%**), vs. Jazan (**53.5%**). |
| **Wages & Education Gap** | **`11K – 24K SAR`** | Average monthly wages scale sharply with education: **5K** (Secondary), **11K** (Bachelor's), **18K** (Master's), and **24K** (Doctorate). Unemployment among graduates concentrates in Business/Admin/Law (**28.8%**) and Education (**15.2%**). |

---

## Dashboard Pages & Visual Walkthrough

### 1. Overview (`نظرة عامة`)
> A comprehensive summary of key Saudi labor market indicators (2021–2026), tracking workforce headcount, employment rates, unemployment trends, and regional participation.

[Overview Page](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/images/01_overview)

### 2. Workforce Distribution (`توزيع القوى العاملة`)
> A detailed breakdown of workforce composition by nationality, major occupational groups, and economic activities, alongside wages, weekly working hours, and graduate unemployment by field of study.

[Workforce Distribution](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/images/02_workforce_distribution)

### 3. Vision 2030 (`رؤية 2030`)
> Tracks national workforce progress toward Saudi Vision 2030 milestones in lowering Saudi unemployment, expanding Saudization, and raising female and private-sector participation.

[Vision 2030 Page](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/images/03_vision_2030)

---

## Data Architecture & Technical Documentation

* **Data Sources:** General Authority for Statistics (**GASTAT**) quarterly labor market releases and General Organization for Social Insurance (**GOSI**) datasets (Q1 2021 – Q2 2026).
* **Data Modeling:** Built around a central DAX `Calender` dimension table and a custom disconnected **`Gender & Nationality`** parameter table (`DATATABLE`) enabling unified demographic filtering across wide-format fact tables without many-to-many ambiguity.
* **Two-Tier DAX Architecture:** Separates base demographic `SWITCH` measures (`_... Value`) from visual-layer `LatestDate` wrappers, YoY time-intelligence calculations, dynamic Arabic chart titles, semantic KPI coloring, and first/last trend-line data labels.

### Project Documentation
* **DAX Measures & UX Layer:** [`Saudi-Labor-Market/dax.md`](https://github.com/hajeromerbashir/Saudi-Labor-Market/tree/main/dax)
* **Power Query (M) ETL Pipeline:** [`Saudi-Labor-Market/power-query-etl.md`](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/power%20query/%23%201.%20ETL%20Pipeline%20Overview)]
* **Arabic-to-English Data Dictionary:** [`Saudi-Labor-Market/dataset/# Data Dictionary & Dataset Description.md`](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/dataset/%23%20Data%20Dictionary%20%26%20Dataset%20Descriptions))

[Data Model](https://github.com/hajeromerbashir/Saudi-Labor-Market/blob/main/images/data%20model%20PBI.PNG))

---

## Analytical & Design Decisions

* **Excluding Wage YoY % Change:** Although initially prototyped, Year-over-Year percentage change for monthly wages was intentionally excluded from KPI cards. Because baseline wages vary widely across demographic segments (as low as 2K–4K SAR for some groups), modest absolute shifts (e.g., ~200 SAR) produce exaggerated percentage swings (3%–10%) that can mislead non-technical audiences.
* **Semantic Model Pruning:** Seven unused prototype sheets from an earlier Q1 2025 draft workbook were audited and removed from the final `.pbix` model to minimize memory footprint and maintain clean lineage.
* **Clutter-Free Trend Visuals:** Vision 2030 line charts use custom DAX measures (`Label - First & Last`) to render data labels strictly on the first and last visible quarters of the selected time range.

---

## Repository Structure

```text
saudi-labor-market-powerbi/
├── README.md                          # English documentation (Default)
├── README.ar.md                       # Arabic documentation
├── .gitignore                         # Ignore temporary Power BI & Excel lock files
├── dashboard/
│   └── Saudi_Labor_Market_2021_2026.pbix
├── data/
│   ├── raw/                           # Original GASTAT & GOSI Excel workbooks
│   └── data-dictionary.md             # Arabic-to-English dataset & column dictionary
├── docs/
│   ├── dax-measures.md                # Full categorized DAX & UX documentation
│   └── power-query-etl.md             # Power Query (M) ETL pipeline & cleaning steps
└── assets/
    ├── 01_overview.png                # Overview page screenshot
    ├── 02_workforce_distribution.png  # Workforce Distribution screenshot
    ├── 03_vision_2030.png             # Vision 2030 Tracker screenshot
    └── data_model_star_schema.png     # Power BI Model view screenshot
