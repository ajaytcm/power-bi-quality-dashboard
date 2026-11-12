# Power BI — Quality & Delivery Dashboard

A one-page Power BI dashboard built from a small weekly quality dataset: defect rate by production line, on-time delivery (OTIF-style), and supplier issues over six weeks.

**Skills shown:** Power BI data loading and shaping, calculated measures (defect rate %, on-time %), line/bar visuals, slicers, and a readable one-page layout.

## Files

- `data/quality_metrics.csv` — the dataset (12 rows: 6 weeks x 2 lines, synthetic sample data).
- `INSTRUCTIONS.md` — step-by-step build instructions, including the exact measures to create.
- `quality_dashboard.pbix` — the finished report file (added after completing the steps).
- `dashboard.png` — a screenshot of the finished page (add it — this is what most visitors will look at).

## Page layout (target)

- **Cards (top):** Overall Defect Rate % · On-Time % · Total Defects · Total Supplier Issues
- **Line chart:** Defect Rate % by week, one line per production line
- **Bar chart:** On-Time % by line
- **Slicer:** Line (and Week if space allows)

## Measures

- `Defect Rate % = DIVIDE(SUM(defects_found), SUM(inspected_units))`
- `On-Time % = DIVIDE(SUM(orders_on_time), SUM(orders_shipped))`
