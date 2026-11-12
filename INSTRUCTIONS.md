# Step-by-Step — Build the Quality Dashboard

Time: about 45 minutes. Tool: Power BI Desktop (free from Microsoft). Data: `data/quality_metrics.csv` in this repo.

## Step 1 — Get the data
1. Open Power BI Desktop → **Get data → Text/CSV** → choose `quality_metrics.csv`.
2. In the preview, check the column types: `week` = Date, the count columns = Whole number. Fix any column Power BI guesses wrong, then **Load**.

## Step 2 — Create the measures
Right-click the table name in the Data pane → **New measure**, and create each of these exactly:

```
Defect Rate % = DIVIDE ( SUM ( quality_metrics[defects_found] ), SUM ( quality_metrics[inspected_units] ) )
```
```
On-Time % = DIVIDE ( SUM ( quality_metrics[orders_on_time] ), SUM ( quality_metrics[orders_shipped] ) )
```
Also create `Total Defects = SUM ( quality_metrics[defects_found] )` and `Total Supplier Issues = SUM ( quality_metrics[supplier_issues] )`.
Select `Defect Rate %` and `On-Time %` and set their format to **Percentage, 1 decimal** (Measure tools → Format).

## Step 3 — Build the KPI cards
Add four **Card** visuals across the top: Defect Rate %, On-Time %, Total Defects, Total Supplier Issues. A card with no measure shows "Blank" — drag the measure into the card's Fields well.

## Step 4 — Trend line chart
Add a **Line chart**: Axis = `week`, Values = `Defect Rate %`, Legend = `line`. Title it "Defect Rate % by Week". Check the story it tells: Line A spikes in the week of 2026-09-21 (22 defects) — the chart should make that spike obvious.

## Step 5 — On-time bar chart
Add a **Clustered bar chart**: Axis = `line`, Values = `On-Time %`. Set the axis range to start near 0.85 if Power BI allows, or leave automatic — note in the README which you chose and why (truncated axes exaggerate differences; for an honest report, starting at 0 is safer).

## Step 6 — Slicer and finishing touches
1. Add a **Slicer** on `line`. Click Line A / Line B and confirm every visual on the page reacts.
2. Give the page a title text box: "Weekly Quality & Delivery — Sample Data".
3. Check every number once against the CSV by hand (spot-check one week in Excel or by eye). A dashboard with one wrong KPI is worse than no dashboard.

## Step 7 — Save and publish to the repo
1. Save as `quality_dashboard.pbix` in this folder.
2. Take a full-page screenshot (View → fit to page, then screenshot) and save it as `dashboard.png`.
3. Upload both files to this repo.

## How to talk about this project in an interview
- "Defect rate is defects divided by inspected units — I use DIVIDE so a week with zero inspections shows blank instead of an error."
- "I spot-check dashboard numbers back to the source file. The dashboard is only as good as the data check behind it."
- "The interesting finding is Line A's spike in the Sep 21 week — in a real review that is where the root-cause questions start."
