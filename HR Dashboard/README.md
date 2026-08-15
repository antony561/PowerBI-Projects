# 👥 HR Dashboard

An interactive Power BI dashboard designed to give HR teams and business leaders a clear, real-time view of workforce health — from headcount and attrition to diversity and departmental performance.

---

## 📌 Overview

Managing a workforce effectively requires visibility across multiple dimensions. This dashboard consolidates key HR metrics into a single, easy-to-navigate report, enabling data-driven decisions around talent retention, hiring, and workforce planning.

---

## 📊 Key Metrics & Visuals

- **Total Headcount** — current employee count with month-on-month trend
- **Attrition Rate** — voluntary and involuntary separations over time
- **Department Breakdown** — headcount and attrition by department or team
- **Tenure Analysis** — employee distribution by length of service
- **Diversity Overview** — gender and age-group breakdowns
- **Hiring vs. Attrition** — net workforce growth over selected periods

---

## 🔍 Features

- **Interactive Slicers** — filter by department, gender, employment type, and date range
- **Drill-through Pages** — click into a department for an individual-level breakdown
- **Conditional Formatting** — highlights departments with high attrition risk
- **Tooltips** — hover over any visual for contextual detail without leaving the page

---

## 🗂️ Files

| File | Description |
|---|---|
| `HR Dashboard.pbix` | Main Power BI report file |
| `HR_Data.xlsx` *(or similar)* | Source dataset used in the report |

> File names may vary slightly — refer to the files present in this folder.

---

## 🛠️ Data Model

The report is built on a flat or lightly relational data model. Key transformations performed in **Power Query** include:

- Parsing hire and termination dates
- Calculating derived columns (e.g., tenure in years, age bands)
- Standardising department and role naming

Key **DAX** measures include:

```dax
Attrition Rate = DIVIDE([Total Leavers], [Average Headcount], 0)
```

---

## 🚀 How to Use

1. Open `HR Dashboard.pbix` in **Power BI Desktop**.
2. If prompted, update the data source path to point to the local data file.
3. Click **Refresh** to load the data.
4. Use the slicers on each page to filter the view to your area of interest.

---

## 📸 Dashboard Preview

<img width="1055" height="599" alt="image" src="https://github.com/user-attachments/assets/b4f7810b-cc55-4a09-aee4-f6db228fb895" />

---

## 💡 Insights This Dashboard Can Answer

- Which departments have the highest attrition?
- How is headcount trending quarter over quarter?
- What is the average tenure of employees who leave?
- How does the gender split vary across seniority levels?
