# Task 3: Dashboard Design
### Sales & Financial Performance Dashboard

## Objective
Design an interactive dashboard for business stakeholders that surfaces sales performance, profitability, and growth trends, and can be filtered by time period, region, category, and channel.

## Tools
Power BI / Tableau (see [Recreating in Power BI / Tableau](#recreating-in-power-bi--tableau) below for a native build; this submission also ships a working HTML/JS prototype built on the same dataset and field mapping).

## Deliverables
| File | Description |
|---|---|
| `Sales_Financial_Dashboard.html` | Interactive dashboard prototype — open directly in any browser |
| `Task3_Dashboard_Summary.pptx` | PPT summary of objective, KPIs, design rationale, and findings |
| `Sales_Financial_Dataset.csv` | Source dataset (order-level transactions) |
| `README.md` | This file |

## Dataset
`Sales_Financial_Dataset.csv` is a synthetic Sales/Financial dataset built in the spirit of typical Kaggle retail datasets, since a specific dataset wasn't provided.

- **Grain:** one row per order
- **Rows:** 16,637 orders
- **Period:** Jan 2023 – Dec 2025 (3 years)
- **Dimensions:** 5 Regions (North, South, East, West, Central) · 5 Categories (Electronics, Apparel, Home & Kitchen, Groceries, Sports & Fitness) · 3 Channels (Online, Retail Store, Distributor)

| Column | Description |
|---|---|
| Order Date | Transaction date |
| Region | Sales region |
| Category | Product category |
| Channel | Sales channel |
| Units Sold | Units in the order |
| Unit Price | Price per unit |
| Sales | Order revenue |
| Cost | Order cost |
| Profit | Sales − Cost |
| Year / Month / Month Name / Quarter | Date parts, precomputed for convenience |
| Profit Margin % | Profit ÷ Sales |

If you have a real sales/financial dataset to substitute, keep the same column names and the dashboard's filter/KPI logic (in the HTML prototype, or when rebuilt in Power BI/Tableau) will work unchanged.

## KPIs Chosen
- **Total Sales** — overall revenue
- **Total Profit** — bottom-line contribution
- **Profit Margin %** — efficiency, not just volume
- **Units Sold** — demand volume
- **Orders** — transaction count (separates volume from basket size)

## Dashboard Structure
The prototype has 4 pages, reached via the left-hand navigation menu:

1. **Overview** — KPI cards, monthly Sales vs. Profit trend, sales share by category, sales by region and channel, top 5 category × region combinations
2. **Sales Trends** — monthly sales trend, monthly profit margin % trend, quarterly sales comparison across years
3. **Regional** — sales & profit by region, top-3 region monthly trend, full region performance table
4. **Category & Channel** — sales by category, channel mix per category (stacked), full category performance table

All KPI cards and charts respond live to the filter chips at the top (Year, Region, Category, Channel) and a **Reset filters** button clears the selection.

## How to View
Open `Sales_Financial_Dashboard.html` directly in a web browser (Chrome, Edge, Firefox, Safari — no server or install required). Use the left nav to switch pages and the filter chips to slice the data.

## Recreating in Power BI / Tableau
To turn this into a native `.pbix` or `.twbx` file:

1. Import `Sales_Financial_Dataset.csv`; add a Date table for time-intelligence (YTD, MoM, YoY measures).
2. Add slicers for Year, Region, Category, and Channel, and connect them to all visuals on each page/sheet.
3. Build the KPI cards using DAX measures (Power BI) or calculated fields (Tableau): `SUM(Sales)`, `SUM(Profit)`, `SUM(Profit)/SUM(Sales)`, `SUM(Units Sold)`, `COUNTROWS`/order count.
4. Recreate the charts using the same field mapping shown in the HTML prototype and PPT summary: monthly line chart (Sales, Profit), donut/pie by Category, bar by Region and Channel, stacked bar for Channel mix by Category.
5. Apply the same color theme throughout for consistency: Navy `#0B3D62` (primary), Teal `#12877F` (secondary), Amber `#F2A93B` (single accent).
6. Add a navigation menu (Power BI: bookmarks + buttons; Tableau: dashboard actions or a navigation object) linking the four pages.
7. Export a PPT summary of the finished dashboard as the second deliverable, or use `Task3_Dashboard_Summary.pptx` as a template.

## Outcome
This submission demonstrates how to choose stakeholder-relevant KPIs, build interactive filtering, layer in time-series analysis, and apply a consistent visual language — the core skills for turning raw sales/financial data into a dashboard that actually informs business decisions.
