# Supply Chain & Inventory Analytics Dashboard

A Power BI dashboard analyzing 100 SKUs across inventory, suppliers, logistics, and product revenue — built to help operations teams prioritize restocking, supplier reviews, and transportation decisions with validated, number-backed KPIs.

## Project Overview
This project consolidates a 100-record, 24-field supply chain dataset into a single-page, interactive Power BI dashboard. It covers inventory value and stock health, order quantity by transportation mode, shipping time by route, supplier lead time and defect rate, and revenue and manufacturing cost by product type — filterable by Location and Vendor Performance Category. Every headline KPI in this README was independently recalculated from the raw CSV in Python and cross-checked against the dashboard.

## Business Problem
Inventory, supplier, logistics, and quality data are typically tracked separately, making it hard to answer questions like: which locations are at stockout risk, which suppliers are underperforming on quality, and which transportation modes are cost-inefficient. This dashboard brings those signals into one view.

## Objectives
- Quantify total inventory value and stock health across locations
- Evaluate supplier lead time and defect rate to flag underperformers
- Compare transportation modes and routes on volume, speed, and cost
- Break down revenue and manufacturing cost by product type
- Surface location-level product-mix differences to guide restocking
- Deliver a filterable, decision-ready dashboard

## Dataset
- **100 SKU-level records, 24 fields** — pricing, inventory, supplier, logistics, manufacturing, and quality data
- **3 product types:** skincare (40), haircare (33), cosmetics (27)
- **5 suppliers**, **5 locations**, **4 transportation modes**, **3 shipping routes**, **3 carriers**
- File: [`supply_chain_data.csv`](supply_chain_data.csv)

## Key KPIs
| KPI | Value | 
|---|---|
| Total Inventory Value | **$243,857 (0.24M)** | 
| Avg Lead Time | **15.96 days (~16.0)** | 
| Stockout Rate | **1.00%** (1 of 100 SKUs) | 
| Stock Status Split | **83% Optimal / 16% Low Stock / 1% Out of Stock** | 
| High Risk Records | 97 (dashboard KPI) | 
| Vendor Performance Category | dashboard slicer | 

## Dashboard Preview
![Supply Chain & Inventory Analytics Dashboard](dashboard-preview.png)

## Key Insights
- **Sea transport moves 38.4% less volume** than the Road/Rail/Air average but costs **24.3% less per shipment** — an underused, cost-efficient mode.
- **Supplier 5's defect rate (2.67%) is 47.8% higher than Supplier 1's (1.80%)**, despite Supplier 1 handling the most volume (27 of 100 SKUs).
- **Bangalore has the highest at-risk stock concentration** — 27.8% of its SKUs are Low or Out of Stock, vs. 8% in Kolkata.
- **77% of SKUs haven't cleared quality inspection** (36% Fail, 41% Pending); Failed SKUs run a 26% higher defect rate than Passed ones.
- **Skincare generates 49.6% more revenue than cosmetics** ($241,628 vs. $161,521).
- **The dashboard's manufacturing-cost-vs-revenue chart is on mismatched scales** (per-unit cost vs. aggregate revenue) and should not be read as a margin.

Full write-up with all 12 quantified insights: [`CASE_STUDY.md`](CASE_STUDY.md) · [`insights.md`](insights.md)

## Business Recommendations
1. Shift measured Road/Rail volume to Sea where timelines allow, to capture the ~24% cost advantage.
2. Open a quality review with Supplier 5; consider rebalancing volume toward Supplier 1.
3. Prioritize Bangalore in the next restocking cycle.
4. Clear the 41-SKU inspection "Pending" backlog and set a turnaround SLA.
5. Expedite restocking for SKU68 (actively selling, zero stock).
6. Set per-location, per-category reorder targets instead of one network-wide rule.

## Analytical Approach
1. **Data profiling & cleaning** — checked dtypes, duplicate/ambiguous columns (two lead-time fields), and scale mismatches in Python (pandas).
2. **KPI design** — defined stock-status thresholds, stockout rate, and total inventory value as auditable calculations.
3. **Dashboard build (Power BI)** — KPI cards, combo chart, 100% stacked bar, and interactive slicers.
4. **Validation** — recalculated every dashboard KPI independently from the raw CSV and reconciled it, flagging any KPI that couldn't be reproduced rather than guessing at its formula.
5. **Extended analysis** — correlation checks, supplier/carrier ranking, and location-level risk breakdowns beyond what's shown on the dashboard face.

## STAR Case Study
- **Situation:** No unified, number-based view connecting inventory, supplier quality, logistics, and revenue across a 5-location, 5-supplier network.
- **Task:** Build a validated Power BI dashboard and back it with an auditable analysis for operational decision-making.
- **Action:** Cleaned and profiled the dataset, defined and validated KPIs, built the dashboard with interactive slicers, and cross-checked every metric against the raw data.
- **Result:** Confirmed all reproducible dashboard KPIs exactly, surfaced 12 additional quantified insights (e.g., a 47.8% supplier defect-rate gap and a 24.3% Sea-shipping cost advantage), and flagged a scale-mismatch issue that would have produced a misleading ~99% "margin" claim if left unchecked.

Full STAR narrative: see [`CASE_STUDY.md`](CASE_STUDY.md#10-star-case-study)

## Tools & Technologies
- **Power BI** — dashboard design, DAX measures, interactive slicers
- **Python (pandas)** — data profiling, KPI validation, correlation analysis
- **CSV/Excel** — source data format

## Limitations
- Small sample (100 records) limits how far percentages generalize.
- `Manufacturing costs` (per-unit) and `Revenue generated` (aggregate) are on different scales and were not netted into a margin.
- `Revenue generated` shows near-zero correlation (r = 0.07) with `Price × Number of products sold`, so it appears to be an independently recorded field.
- Two undocumented lead-time columns exist (`Lead times` vs. `Lead time`); this analysis used `Lead times` since it reconciles with the dashboard's KPI.
- "High Risk Records" and "Vendor Performance Category" could not be validated against the raw CSV and are reported as dashboard-native metrics.

Full limitations list: [`CASE_STUDY.md`](CASE_STUDY.md#12-limitations)

## Future Improvements
- Source a data dictionary to resolve column ambiguities.
- Add a time dimension for trend analysis.
- Obtain production-volume-matched cost data to enable a valid margin analysis.
- Document the "High Risk Records" and "Vendor Performance Category" DAX logic.
- Expand the dataset for more statistically reliable comparisons.

## Project Files
```
01-Supply-Chain-Inventory-Analytics/
├── README.md
├── Supply_Chain_Inventory_Analytics.pbix
├── supply_chain_data.csv
├── dashboard-preview.png
├── CASE_STUDY.md
└── insights.md
```
