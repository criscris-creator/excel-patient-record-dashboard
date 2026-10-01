# Historical Patient Record Dashboard (Excel)

> An interactive Excel dashboard that turns 2011-2022 hospital patient records into an executive-ready view of encounters, patient mix, payers, procedures, and admissions trends.

<img width="765" height="433" alt="dashboard" src="https://github.com/user-attachments/assets/60fa75c7-7837-4070-96a8-12282fd47978" />


**Capstone project** | Datasense Analytics | Built entirely in Microsoft Excel using PivotTables, PivotCharts, slicers, and a timeline

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Questions](#business-questions)
- [Dashboard at a Glance](#dashboard-at-a-glance)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Dataset and Data Model](#dataset-and-data-model)
- [How the Workbook Is Built](#how-the-workbook-is-built)
- [Skills Demonstrated](#skills-demonstrated)
- [Repository Contents](#repository-contents)
- [How to Use the Dashboard](#how-to-use-the-dashboard)
- [Limitations](#limitations)
- [Author](#author)

---

## Project Overview

Hospital records hold a huge volume of transactional activity that is hard to read as raw tables. Leadership needs a compact view that answers practical questions:

- What does the historical patient population look like?
- How is care being used, and how has demand changed over time?
- Which payers and procedures dominate activity?
- Where should the hospital focus its attention?

This dashboard covers **2011-2022** and moves from headline KPIs, to diagnostic charts, to a short **Key Insights** panel, so a decision-maker can understand the story without digging through the data.

## Business Questions

The dashboard was designed to answer six questions. Each one maps to a specific visual.

| Focus | Business question | Where it is answered |
|-------|-------------------|----------------------|
| Utilization | How many encounters and procedures are being recorded, and what is the average visit length? | KPI cards: Total Encounters, Total Procedures, Avg. Visit Length |
| Demand trend | How do admissions change over time, and which year has the highest demand? | Admissions line chart and Timeline slicer |
| Population mix | What share of the population is senior versus adult, and how does the gender mix differ by age group? | Age Group & Gender chart and the Age Group and Gender slicers |
| Payer mix | Which payers have the largest volumes, and how significant is the uninsured segment? | Payers chart and Payer slicer |
| Procedure demand | Which procedures have the largest volumes and deserve capacity or workflow attention? | Top 10 Procedures chart |
| Decision support | Can the dashboard surface the most important findings without users interpreting every chart? | Key Insights panel |

## Dashboard at a Glance

| KPI | Value |
|-----|-------|
| Total Encounters | **27,891** |
| Total Patients Served | **974** |
| Average Visit Length | **0.31** |
| Total Procedures | **47,701** |

**Interactive filters:** Timeline (year range), Age Group, Gender, and Payer.

**Visuals:**

- Admissions trend by year
- Top 10 procedures
- Age group and gender breakdown
- Encounters by payer
- Key Insights panel

## Key Insights

1. **Seniors dominate activity.** Senior (65+) records account for 21,446 of 27,891 encounters, about **77%**, versus 6,445 for adults (18-64).
2. **Admissions peaked in 2014.** The trend reaches its highest point in 2014, a useful benchmark for staffing and capacity planning.
3. **Procedure demand is concentrated.** The top procedure is *Assessment of health and social care needs* (about 4,596 records), followed by depression screening, substance-use assessment, Morse Fall Scale assessment, and medication reconciliation.
4. **Payer mix is highly uneven.** Medicare (11,371) and No Insurance (8,807) are far larger than any named commercial payer.
5. **Heavy repeat utilization.** 27,891 encounters across 974 patients is roughly **28.6 encounters per patient** (derived from the KPI cards).

## Recommendations

These are proposed opportunities based on the dashboard, not claims of realized outcomes.

1. **Build a senior-centered care program** with fall-risk assessment, medication reconciliation, social-needs screening, and discharge planning.
2. **Turn screening into action.** Link fall-risk, depression, and social-needs screenings to standard follow-up and referral workflows.
3. **Use the 2014 peak as a stress-test benchmark** for staffing, beds, and support services.
4. **Investigate high-utilization patients** to see whether repeat visits are driven by chronic disease, social barriers, or avoidable utilization.
5. **Develop a targeted uninsured-patient strategy** with financial counseling, eligibility screening, and benefits navigation.
6. **Measure outcomes, not just volume** (falls per 1,000 patient days, 30/90-day revisit rate, referral completion, uninsured rate).

The full case study with the impact table and measurement plan is in [`docs/Case_Study.pdf`](docs/Case_Study.pdf).

## Dataset and Data Model

The workbook includes a data dictionary sheet and five source tables:

| Table | Description |
|-------|-------------|
| `encounters` | Patient encounters: start/stop time, class (ambulatory, emergency, inpatient, wellness, urgent care), costs, payer coverage, reason |
| `patients` | Patient demographics: birth date, gender, race, ethnicity, location |
| `procedures` | Procedures performed during encounters, with code, description, and base cost |
| `payers` | Insurance payer details |
| `organizations` | Hospital/organization details |

Tables are linked by keys (`Patient`, `Payer`, `Organization`, `Encounter`) as described in the `data_dictionary` sheet.

**Source:** Dataset provided by Datasense Analytics as part of the capstone program.

## How the Workbook Is Built

The `.xlsb` workbook has 8 sheets:

| Sheet | Purpose |
|-------|---------|
| `Dashboard` | The final interactive dashboard (charts, KPI cards, slicers, timeline) |
| `Pivots` | PivotTables that feed the dashboard visuals |
| `data_dictionary` | Field definitions for every table |
| `patients`, `procedures`, `payers`, `organizations`, `encounters` | Source data |

Under the hood:

- **7 PivotTables** and **7 charts** drive the visuals
- **3 slicers** (Age Group, Gender, Payer Name) and **1 timeline** control the whole dashboard
- Formulas used include `XLOOKUP`, `IFS`, `UNIQUE`, and `CONCAT`
- Built entirely in Microsoft Excel using PivotTables, with no Power BI or DAX

## Skills Demonstrated

- Data cleaning and preparation
- Working with a multi-table dataset (encounters, patients, procedures, payers, organizations)
- PivotTables and PivotCharts
- Slicers and timelines for interactivity
- Lookup and logical formulas (`XLOOKUP`, `IFS`, `UNIQUE` and `CONCAT`)
- KPI card design and dashboard layout
- Turning analysis into business recommendations
- Healthcare analytics (utilization, payer mix, procedures)

## Repository Contents

```
.
├── README.md
├── dashboard.png                  # Dashboard screenshot
├── Patient_Dashboard.xlsb         # Excel dashboard workbook
├── docs/
│   └── Case_Study.pdf             # Full written case study
└── demo/
    └── Dashboard_Demo.mp4         # Short demo video
```

## How to Use the Dashboard

1. Download `Patient_Dashboard.xlsb` (GitHub cannot preview Excel files in the browser).
2. Open it in **Microsoft Excel for desktop**. Excel 365 or 2021 is recommended because the workbook uses `XLOOKUP` and `UNIQUE`.
3. Go to the **Dashboard** sheet.
4. Use the **Timeline**, **Age Group**, **Gender**, and **Payer** slicers to filter every chart and KPI at once.
5. If prompted, click **Enable Content**. If the PivotTables look stale, go to **Data > Refresh All**.

## Limitations

- Average visit length is shown as 0.31 on the dashboard; the unit depends on how the visit length field was calculated.
- The 28.6 encounters per patient figure is derived from the KPI cards and should be validated against the source grain before operational use.
- Recommendations are proposals based on historical data and have not been tested.

## Author

**Maria Clarissa Cristobal**
Data Analytics capstone, Datasense Analytics

- LinkedIn: https://www.linkedin.com/cris-cristobal
- Email: mclarissadiaz@gmail.com

---

*If you found this project useful, feel free to star the repository.*
