# 💰 Sales Dashboard

An interactive Power BI sales performance dashboard built on a sample dataset of 100 orders across 12 customers — demonstrating end-to-end report design from raw data to polished visuals, covering revenue analysis, product performance, and regional and category trends.

---

## 📌 Overview

This dashboard simulates a real-world sales reporting scenario using a randomly generated dataset of technology product sales. It covers the full Power BI workflow: data import, transformation in Power Query, DAX measure creation, and report layout design — making it a strong portfolio piece for end-to-end BI development.

---

## 📊 Key Metrics & Visuals

- **Total Revenue** — overall sales figure across the full date range
- **Total Orders** — count of transactions with order volume trend
- **Average Order Value (AOV)** — revenue per transaction by category
- **Revenue by Country & State** — geographic breakdown of sales performance
- **Top Products** — best-performing products ranked by revenue
- **Category Analysis** — sales, order count, and average value across product categories
- **Annual Sales Trend** — year-over-year revenue growth

---

## 🔍 Features

- **Date Slicer** — filter all visuals by year or custom date range
- **Country & Category Filters** — drill into specific markets or product groups
- **KPI Cards** — at-a-glance summary of total sales, order count, and AOV
- **Bar, Line & Map Visuals** — varied chart types for clear data storytelling
- **Tooltips** — hover for additional context on any data point

---

## 🗂️ Files

| File | Description |
|---|---|
| `dashboard.pbix` | Main Power BI report file |
| `dataset/orders.csv` | 100 order-level transaction records |
| `dataset/customers.csv` | 12 customer records with location data |
| `sales-dashboard.pdf` | Static PDF export of the dashboard |

---

## 🛠️ Data Model

The report uses a simple star-style model with an orders fact table joined to a customers dimension table on `customer_id`. Key Power Query steps include standardising date formats and parsing semicolon-delimited source files. Key DAX measures include:

```dax
Total Revenue = SUM(Orders[sales])

YoY Revenue Growth % =
DIVIDE(
    [Total Revenue] - CALCULATE([Total Revenue], DATEADD('Date'[Date], -1, YEAR)),
    CALCULATE([Total Revenue], DATEADD('Date'[Date], -1, YEAR)),
    0
)
```

---

## 🚀 How to Use

1. Open `dashboard.pbix` in **Power BI Desktop**.
2. If prompted, update the data source path to point to the `dataset/` folder.
3. Click **Refresh** to load the data.
4. Explore the report using slicers and the page navigation bar.

---

## 📈 Key Insights

The dataset covers **100 orders** placed by **12 customers** across four countries, generating **$102,530 in total revenue**.

**Laptops drive over half of all revenue despite not being the most ordered category**
Laptops account for **$52,435 (51.1% of total revenue)** from just 27 orders — the second-highest order volume behind Smartphones. This gives Laptops an average order value of **$1,942**, the highest of any category. By contrast, Accessories generate 19 orders but only $2,709 in revenue (average $143 per order), making them a volume driver with minimal revenue impact.

**The US dominates, but China is a strong second market**
The United States accounts for **$66,024 (64.4%)** of total revenue, with China a clear second at $30,754 (30%). Germany and India contribute $3,210 and $2,543 respectively. At a state level, Shanghai ($17,123), New Jersey ($16,314), and California ($15,927) are the top three territories by revenue.

**Dell XPS 15 is the single best-performing product**
The Dell XPS 15 generates **$24,501** in revenue — nearly double the next product, the ThinkPad X1 ($13,397). The top five products (Dell XPS 15, ThinkPad X1, Galaxy S24, HP Spectre x360, iPad Air 6) together account for **$59,341 (57.9%)** of total revenue, showing that a small product range is driving the majority of value.

**Revenue has grown consistently year over year**
Sales grew from **$21,316 in 2024** to **$34,451 in 2025**, and reached **$46,763 in 2026** — representing a year-over-year growth of approximately 35–36% across both periods. This upward trajectory across all three years demonstrates consistent demand growth in the dataset.

**Tablets punch above their weight in average order value**
Tablets rank third by revenue ($18,701) from only 14 orders, giving them an average order value of **$1,336** — second only to Laptops. This suggests Tablet buyers are purchasing higher-value items (such as the iPad Air 6) and represent a high-value segment despite lower order frequency.

> **Note:** The dataset is randomly generated and does not represent any real organisation or individuals. It is used purely for demonstration and portfolio purposes.
