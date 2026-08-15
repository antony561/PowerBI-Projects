# 🏥 Patient Waitlist Dashboard

An interactive Power BI dashboard built to monitor and analyse patient waitlist trends across healthcare services — helping administrators and clinical leads manage demand, reduce wait times, and allocate resources effectively.

---

## 📌 Overview

Long patient waitlists are one of the most pressing challenges in healthcare. This dashboard provides a structured view of waitlist volumes, wait time distributions, and case-type breakdowns, enabling informed decisions about capacity and prioritisation.

---

## 📊 Key Metrics & Visuals

- **Total Waitlist Volume** — current number of patients waiting, with period-over-period comparison
- **Average & Median Wait Time** — wait time statistics across specialties and case types
- **Case Type Breakdown** — split between Inpatient, Outpatient, and Day Case
- **Specialty Analysis** — waitlist volumes by medical specialty or department
- **Age Profile** — patient age-band distribution across the waitlist
- **Monthly Trend** — waitlist growth or reduction over time

---

## 🔍 Features

- **Dynamic Slicers** — filter by specialty, case type, age band, and date range
- **Summary vs. Detail View** — toggle between high-level KPIs and granular breakdowns
- **Trend Lines** — visualise waitlist movement across months
- **Conditional Formatting** — flags specialties exceeding target wait thresholds

---

## 🗂️ Files

| File | Description |
|---|---|
| `Patient Waitlist Dashboard.pbix` | Main Power BI report file |
| `Inpatient_Data.csv` *(or similar)* | Inpatient waitlist source data |
| `Outpatient_Data.csv` *(or similar)* | Outpatient waitlist source data |

> File names may vary slightly — refer to the files present in this folder.

---

## 🛠️ Data Model

The report combines inpatient and outpatient data into a unified model. Key **Power Query** steps include:

- Appending inpatient and outpatient tables
- Parsing and standardising date columns
- Creating age band and wait-time band calculated columns

Key **DAX** measures include:

```dax
Avg Wait Time (Days) = AVERAGEX(Waitlist, Waitlist[Wait Time Days])

Latest Month Waitlist = 
CALCULATE(
    COUNT(Waitlist[Patient ID]),
    Waitlist[Archive Date] = MAX(Waitlist[Archive Date])
)
```

---

## 🚀 How to Use

1. Open `Patient Waitlist Dashboard.pbix` in **Power BI Desktop**.
2. If prompted, update the data source path to point to the local data files.
3. Click **Refresh** to load the latest data.
4. Use the page navigation and slicers to explore different views.

---

## 📸 Dashboard Preview

<img width="1154" height="656" alt="image" src="https://github.com/user-attachments/assets/df28cd95-bbd8-4dbf-8908-6ba678431f1b" />

---

## 💡 Insights This Dashboard Can Answer

- Which specialties have the longest average wait times?
- Is the total waitlist growing or shrinking month over month?
- What proportion of the waitlist is Inpatient vs. Outpatient?
- Which age groups make up the largest share of patients waiting?
