# QLD Healthy Weight Dashboard

![Dashboard Overview](assets/overview-preview.png)

A population health analytics dashboard that classifies patient BMI records using CDC (Centers for Disease Control and Prevention) standards — built as both a Python-generated PDF report and a native Power BI dashboard, using the same underlying cleaning and classification logic in both.

## What This Project Is

This project profiles and classifies 151,524 de-identified patient BMI records across Queensland hospital facilities, applying CDC classification standards to segment patients into Underweight, Healthy Weight, Overweight, and Obesity categories — for both adults and children, using the correct age-appropriate method for each.

It's a personal portfolio project demonstrating an end-to-end analytics workflow: raw data → cleaning → clinical classification logic → relational data modelling → an interactive multi-page BI dashboard.

## The Problem It's Solving

Raw patient weight data alone doesn't answer basic public-health-planning questions:

- Which regions or facilities have the highest concentration of overweight/obese patients?
- Is the pattern improving or worsening over time?
- Where would a targeted intervention program do the most good?

This dashboard turns raw, unclassified records into an actionable planning tool — the kind used to decide where to direct funding and intervention programs, rather than spreading resources evenly regardless of need.

## The Dataset

- **151,524 raw patient records**: facility, age, suburb, postcode, weight, height, BMI, and measurement date, spanning 2015–2021.
- A CDC growth chart reference file (percentiles by age-in-months and gender), used specifically for classifying children.
- **Data note**: this particular extract is 100% female patients — a property of the data source, not a filtering choice made in this analysis.

> **The raw and cleaned patient data files are not included in this repository.** They contain individual-level health records and aren't mine to redistribute publicly. The pipeline below documents exactly what was done to them; see `docs/project-writeup.md` for the full data description if you need to reconstruct a compatible input file.

## Data Cleaning

- Removed records with implausible BMI values (kept only 8–90).
- Removed records with implausible ages (kept only 0–105).
- Result: 314 of 151,524 raw records dropped (0.2%), leaving **151,210 clean records**.
- Built a single usable record date per patient, extracted `Year` for trend analysis, and bucketed patients into age groups (0-18 through 90-110).

Implemented twice, in two different tools, to demonstrate the same logic in both:
- **Python/pandas** — see `scripts/clean_and_classify.py`
- **Power Query (M) + DAX** — native to the Power BI file itself, no external script dependency

## BMI Classification — CDC Standard

**Adults (≥20 years):** fixed cutoffs.
| Category | BMI Range |
|---|---|
| Underweight | < 18.5 |
| Healthy Weight | 18.5 – 24.9 |
| Overweight | 25.0 – 29.9 |
| Obesity | ≥ 30.0 |

**Children (2–19 years):** CDC age- and gender-specific growth chart percentiles, since a fixed BMI cutoff isn't clinically valid for growing children.
| Category | Percentile |
|---|---|
| Underweight | < 5th |
| Healthy Weight | 5th – 85th |
| Overweight | 85th – 95th |
| Obesity | ≥ 95th |

Since the source data only had age in whole years, age-in-months was approximated as `(age in years × 12) + 6` before matching to the nearest percentile row by age and gender.

**Result:** 122,419 records classified via the adult method, 28,791 via the child percentile method.

**Overall breakdown:**
| Category | Count | % |
|---|---|---|
| Healthy Weight | 55,249 | 36.5% |
| Overweight | 37,482 | 24.8% |
| Obesity | 52,169 | 34.5% |
| Underweight | 6,310 | 4.2% |

## Facility → Hospital and Health Service (HSS) Mapping

Facility codes (e.g. `PAH`, `TTH`, `GCUH`) were mapped to their full name and Hospital and Health Service region using public Queensland Health facility records. Two facility codes (`CASL`, `RCH`), each appearing only once in the dataset, couldn't be confidently matched and are transparently labelled **"Other / Unmapped"** rather than guessed.

## Dashboard Structure

| Page | Content |
|---|---|
| Overview | KPI cards, classification donut chart, patient volume by facility and year |
| Top 15 Suburbs | Ranked bar chart plus a full searchable suburb table |
| Healthy Weight Summary | Healthy-weight rate by year, facility, and age group |
| Obese & Overweight Summary | Overweight/Obesity/Underweight breakdown by year, facility, and age group |
| Classification by HSS | Regional (HSS-level) breakdown, including a treemap view |
| Report Info | Full methodology and dataset limitations |
| Dictionary | Plain-language definitions of every term used |

## Key Insights

- Roughly 1 in 3 patients fall in the Healthy Weight range (36.5%), while Overweight and Obesity combined account for the majority of records (59.3%).
- Classification rates vary meaningfully by facility, HSS region, and age group — the burden isn't evenly spread.
- Correct age-based classification (adult vs. child methods) means program design can genuinely differ by age group, rather than relying on a one-size-fits-all cutoff that's clinically incorrect for children.

## More Screenshots

| Top 15 Suburbs | Classification by HSS |
|---|---|
| ![Top 15 Suburbs](assets/top15-suburbs-preview.png) | ![HSS Breakdown](assets/hss-preview.png) |


## Tools Used

- **Python** (pandas, numpy) — initial data cleaning and classification pipeline
- **Power BI** (Power Query / M, DAX) — native rebuild of the same pipeline plus the interactive dashboard
- **matplotlib** — PDF report generation

## Limitations

- This dataset is female-only — a characteristic of this particular data source, not a filtering decision.
- Population/ABS census benchmarking was intentionally excluded, to keep every figure traceable to patient-level source data.
- Two facility codes couldn't be confidently mapped to their HSS region and are disclosed as "Other / Unmapped."
- Child age was only available in whole years, so age-in-months for the percentile lookup is a mid-year approximation.
