# Key Insights — Supply Chain & Inventory Analytics

All figures independently recalculated from `supply_chain_data.csv` (100 SKUs) and cross-checked against the Power BI dashboard. See `CASE_STUDY.md` for full methodology, STAR narrative, and limitations.

1. **Sea transport: high cost efficiency, low utilization.** Sea moves 853 order units — 61.5% of Road's 1,386, and 38.4% below the Road/Rail/Air average — while costing 24.3% less per shipment ($417.82 vs. $552.28 average). → Pilot shifting non-urgent volume to Sea.

2. **Supplier 5 lags on quality by 47.8%.** Avg defect rate: Supplier 5 = 2.67%, Supplier 1 = 1.80% (the lowest, and highest-volume, supplier at 27 SKUs). → Open a corrective-action review with Supplier 5.

3. **Bangalore has the highest at-risk stock share.** 27.8% of Bangalore's 18 SKUs are Low or Out of Stock, vs. 8% in Kolkata (25 SKUs). → Prioritize Bangalore in the next restock cycle.

4. **77% of SKUs have not cleared quality inspection.** 36% Fail, 41% Pending, 23% Pass. Failed SKUs carry a 26.0% higher defect rate (2.57% vs. 2.04%) than Passed ones. → Clear the Pending backlog first; set an inspection SLA.

5. **Skincare outperforms cosmetics by 49.6% in revenue.** $241,628 vs. $161,521, on a 48% larger SKU count (40 vs. 27). → Evaluate expanding skincare assortment.

6. **The one stockout is an active revenue SKU.** SKU68 (haircare, Bangalore, Supplier 2): $3,550 in recorded revenue, 0 units in stock. → Expedite replenishment for this SKU specifically.

7. **Carrier B leads on both cost and speed.** $5.51 avg cost, 5.30-day avg time, already 43% of shipments — vs. $5.55–$5.60 and 6.0–6.1 days for Carriers A/C. → Shift more volume to Carrier B.

8. **Route C is 12.8% faster than Route A but carries the least volume.** 5.25 vs. 6.02 days, on 20 vs. 43 shipments. → Assess capacity to route more shipments via C.

9. **Kolkata: 31.1% of total inventory value and the healthiest stock mix.** $75,796 of $243,857 total; only 8% of its SKUs are Low Stock, none Out of Stock. → Use Kolkata's replenishment cadence as the network benchmark.

10. **Product mix varies sharply by location.** Skincare is 44.2% of Kolkata's stock but cosmetics is 50.6% of Mumbai's. → Set per-location, per-category reorder targets, not one network-wide rule.

11. **Manufacturing cost and revenue are on incompatible scales.** Summed manufacturing cost ($1,100–$2,000/category) vs. summed revenue ($160K–$240K/category) implies a ~99% "margin" that is a data-definition artifact (per-unit vs. aggregate fields), not a real number. → Don't report this as margin; source matched cost/revenue data first.

12. **Revenue is statistically unrelated to price × units sold (r = 0.07).** → Confirm with the data source what `Revenue generated` actually represents before using it in pricing analysis.

---

### Dashboard KPIs flagged as non-reproducible
- **High Risk Records (97):** no combination of raw columns reproduces this value; reported as dashboard-native (likely a multi-condition DAX measure).
- **Vendor Performance Category:** used as a dashboard slicer but not present as a raw column; cannot be validated against the CSV.
