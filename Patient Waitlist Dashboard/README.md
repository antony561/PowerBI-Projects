# 🏥 Patient Waitlist Dashboard

An interactive Power BI dashboard tracking patient waitlist volumes, wait time distributions, and specialty-level trends across inpatient and outpatient services from 2018 to 2021 — covering over **24.6 million patient records**.

---

## 📌 Overview

Long patient waitlists are one of the most pressing challenges in healthcare. This dashboard provides a structured view of waitlist volumes, case-type breakdowns, and year-over-year trends, enabling hospital administrators and clinical leads to make informed decisions about capacity, staffing, and prioritisation.

---

## 📊 Key Metrics & Visuals

- **Total Waitlist Volume** — combined inpatient and outpatient patients, with period-over-period comparison
- **Case Type Split** — breakdown between Day Case, Inpatient, and Outpatient
- **Top Specialties** — highest-volume specialties ranked by total patients waiting
- **Time Band Distribution** — proportion of patients waiting within each wait time range (0–3 months through 18+ months)
- **Age Profile** — patient distribution across 0–15, 16–64, and 65+ age bands
- **Annual Trend** — year-over-year waitlist movement from 2018 to 2021

---

## 🔍 Features

- **Dynamic Slicers** — filter by case type, specialty, age band, adult/child, and year
- **Summary vs. Detail View** — toggle between high-level KPIs and granular specialty breakdowns
- **Specialty Mapping** — specialties grouped into broader clinical categories (e.g., Heart, Brain, Bones) via a mapping table for easier navigation
- **Trend Lines** — visualise waitlist movement across monthly archive snapshots
- **Conditional Formatting** — flags specialties exceeding typical wait thresholds

---

## 🗂️ Files

| File | Description |
|---|---|
| `Patient Waitlist.pbix` | Main Power BI report file |
| `Dataset/Inpatient/` | IN_WL CSVs for 2018–2021 |
| `Dataset/Outpatient/` | Op_WL CSVs for 2018–2021 |
| `Dataset/Mapping_Specialty.csv` | Specialty-to-group mapping reference table |
| `Patient Waitlist.pdf` | Static PDF export of the dashboard |

---

## 🛠️ Data Model

The inpatient and outpatient tables are appended in Power Query to form a unified waitlist fact table, joined to the specialty mapping reference. Key DAX measures include:

```dax
Latest Month Waitlist =
CALCULATE(
    SUM(All_Data[Total]),
    All_Data[Archive_Date] = MAX(All_Data[Archive_Date])
)

Avg Wait Time (Months) = AVERAGEX(All_Data, All_Data[Time_Band_Midpoint])
```

---

## 🚀 How to Use

1. Open `Patient Waitlist.pbix` in **Power BI Desktop**.
2. If prompted, update the data source folder path to point to the `Dataset/` directory.
3. Click **Refresh** to load the data across all years.
4. Use the slicers and page navigation to explore trends by specialty, case type, or year.

---

## 📸 Dashboard Preview

<img width="1154" height="656" alt="image" src="https://github.com/user-attachments/assets/df28cd95-bbd8-4dbf-8908-6ba678431f1b" />

---

## 📈 Key Insights

The dashboard covers **2018 to 2021** and analyses approximately **2.9 million inpatient** and **21.7 million outpatient** patient records — a combined total of over **24.6 million waitlist entries**.

**Outpatient demand dwarfs inpatient by a factor of 7**
Across the full period, outpatient waitlists totalled approximately 21.7 million patient instances versus 2.9 million for inpatient, highlighting that the volume challenge in healthcare is predominantly at the outpatient level. Outpatient services account for roughly 88% of total waitlist pressure.

**Waitlists grew year over year before a sharp 2021 drop**
Inpatient waitlist volumes grew from 911,582 in 2018 to a peak of 923,251 in 2020, before falling sharply to 242,365 in 2021. Outpatient volumes similarly grew from 6.1 million (2018) to 7.1 million (2020) and dropped to 1.9 million in 2021. This sharp fall in 2021 most likely reflects data that is only partially captured for that year rather than a true reduction in demand.

**Orthopaedics and ENT lead both inpatient and outpatient queues**
For inpatient services, General Surgery (427,447), Orthopaedics (416,985), and Urology (367,688) carry the heaviest waitlists. For outpatient, Orthopaedics (2.6M) and ENT (2.6M) are almost equal at the top, followed by Dermatology (1.7M) and Ophthalmology (1.7M). These four specialties consistently represent the highest-pressure areas across both service types.

**Day Cases make up the majority of inpatient waitlist entries**
Of the 2.9 million inpatient records, approximately **2.06 million (71%) are Day Cases** and 845,000 (29%) are overnight Inpatient stays. This is an important distinction for capacity planning — Day Case demand can often be addressed through theatre scheduling and procedure throughput rather than bed capacity.

**Working-age adults (16–64) dominate inpatient waitlists**
The 16–64 age band accounts for **1.67 million inpatient records (58%)**, followed by patients aged 65+ at 963,000 (33%), and children aged 0–15 at 268,000 (9%). The high share of elderly patients is significant for discharge planning and post-acute care resourcing.

**Most patients are waiting under 6 months — but long waits are significant**
The largest time band is 0–3 months (1.04M inpatient records), with 3–6 months second (658K). However, **18+ month waits account for 242,000 records**, indicating a persistent cohort of patients experiencing very long waits — a key area for clinical prioritisation and intervention.
