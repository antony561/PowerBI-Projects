# 👥 HR Dashboard

An interactive Power BI dashboard providing HR teams and business leaders with a clear view of workforce health — covering headcount, attrition risk, diversity, and departmental performance across 1,480 employees.

---

## 📌 Overview

Managing a workforce effectively requires visibility across multiple dimensions. This dashboard consolidates key HR metrics into a single, easy-to-navigate report, enabling data-driven decisions around talent retention, hiring, and workforce planning.

---

## 📊 Key Metrics & Visuals

- **Total Headcount** — current employee count with period-over-period trend
- **Attrition Rate** — voluntary and involuntary separations with department breakdown
- **Department Breakdown** — headcount, attrition, and income by department
- **Age Group Analysis** — attrition rate across five age bands (18–25 through 55+)
- **Overtime Impact** — attrition comparison between overtime and non-overtime employees
- **Gender & Marital Status** — workforce composition and how these factors relate to attrition
- **Job Role Breakdown** — which roles experience the most turnover

---

## 🔍 Features

- **Interactive Slicers** — filter by department, gender, employment type, and age group
- **Drill-through Pages** — click into a department for a role-level breakdown
- **Conditional Formatting** — highlights departments and roles exceeding attrition thresholds
- **KPI Cards** — at-a-glance attrition rate, headcount, and average income
- **Tooltips** — hover over any visual for contextual detail without leaving the page

---

## 🗂️ Files

| File | Description |
|---|---|
| `HR Analysis.pbix` | Main Power BI report file |
| `Dataset.csv` | Source HR dataset (1,480 employee records) |
| `HR Analysis.pdf` | Static PDF export of the dashboard |

---

## 🛠️ Data Model

The report is built on a single flat table with derived columns calculated in Power Query and DAX. Key transformations include parsing age bands, job level groupings, and salary slabs. Key DAX measures include:

```dax
Attrition Rate = DIVIDE([Total Leavers], [Total Employees], 0)
```

---

## 🚀 How to Use

1. Open `HR Analysis.pbix` in **Power BI Desktop**.
2. If prompted, update the data source path to point to `Dataset.csv`.
3. Click **Refresh** to load the data.
4. Use the slicers on each page to filter by department, gender, or age group.

---

## 📸 Dashboard Preview

<img width="1055" height="599" alt="image" src="https://github.com/user-attachments/assets/b4f7810b-cc55-4a09-aee4-f6db228fb895" />

---

## 📈 Key Insights

The analysis covers **1,480 employees** and reveals several meaningful patterns in workforce attrition and composition:

**Overall Attrition**
The organisation has an overall attrition rate of **16.1%** — meaning roughly 1 in 6 employees has left. This is a notable figure and signals areas where targeted retention strategies could have a significant impact.

**Sales is the highest-risk department**
The Sales department has the highest attrition rate at **20.7%**, followed by Human Resources at 19.0% and Research & Development at 13.8%. While R&D accounts for the largest raw number of departures (133 employees), proportionally Sales is where the organisation is losing the most talent relative to its size.

**Young employees are leaving at a disproportionate rate**
Employees aged **18–25 have an attrition rate of 35.8%** — more than double the company average. This drops sharply to 19.0% for the 26–35 age band and falls further for older groups. This suggests onboarding, early career development, or compensation expectations may need to be addressed for entry-level hires.

**Overtime is a strong attrition predictor**
Employees who work overtime leave at a rate of **30.6%**, compared to just 10.4% for those who do not. This is one of the starkest findings in the dataset and points directly to workload management and burnout as key drivers of turnover.

**Single employees leave at twice the rate of married employees**
Single employees have an attrition rate of **25.4%** versus 12.4% for married employees. This may reflect differences in stability, flexibility expectations, or career mobility at different life stages.

**Laboratory Technicians and Sales Executives account for the most departures**
By job role, **Laboratory Technicians (62 departures)** and **Sales Executives (58 departures)** are the top two roles by headcount lost, followed by Research Scientists (47) and Sales Representatives (33). These roles would benefit most from targeted retention programmes.

**Gender composition is skewed male**
The workforce is **60% male (889)** and **40% female (591)**. Whether attrition rates differ significantly between genders is worth exploring as a further lens on retention equity.


