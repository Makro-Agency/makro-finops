# Excel Model Structure: Makro_Agency_Financial_Planner.xlsx

## Overview
9-tab financial planning model for Makro Agency (~20 people, Shopify Plus B2B/DTC agency). Built by AI (Claude 4.4/4.5), never fully recalculated in Excel — many formula cells return None/uncached.

## Tab 1: Setup (Input Sheet)
- Fiscal Year: 2026
- Owner Market-Based Wage: $20,000/mo
- Profit Target: 30%
- Stretch Profit Target: 35%
- Blended Billable Rate: $180/hr
- Std Hours/Month: 160
- Payroll Burden Rate: 11%
- Tax Reserve Rate: 40%
- Core Capital Target: 3 months opex
- DSO Target: 30 days
- Default Deposit: 20%
- Pipeline stage probabilities: Lead 10%, Discovery 25%, Proposal 50%, Negotiation 75%, Contract 90%, Won 100%
- Utilization targets: Senior 75%, Mid 80%, Junior 90%

## Tab 2: People (22 people listed)
Columns: Person/Role, Worker Type (Payroll/Contractor), Level, Role Bucket, Billable Y/N, Util Target %, Start Month, End Month, Monthly Cost, Status, Notes

Key people:
- Owner (CEO/Sales) — Payroll, Senior, Sales, 30% util
- Isabel Maier — Payroll, Mid, AM, 50% util, $9,583/mo
- Olusegun — Payroll, Mid, AM, 50% util, $7,917/mo
- Rahul Parmar — Contractor, Senior, G&A, 50% util, $9,570/mo (no end date — ongoing)
- Nathan V — Contractor, Senior, Dev, 70% util, $3,296/mo
- Luis — Contractor, Mid, Dev, 70% util, $7,425/mo
- Nick — Contractor, Mid, Dev, 70% util, $3,507/mo
- Alexis — Contractor, Mid, G&A, Non-billable, $3,021/mo
- Jose (Bookkeeper) — Contractor, Mid, G&A, Non-billable, $1,627/mo
- Lisania (Marketing) — Payroll, Mid, Marketing, Non-billable, $4,167/mo
- Plus ~10 more devs/PMs at various rates

Formula section (rows 28-42): Monthly totals for Payroll, Contractors, Total Labor, Payroll Burden, Total People Cost
Capacity section (rows 36-42): Billable FTE, Total FTE, Available Hours, Target Billable Hours, Implied Revenue Capacity

FORMULA PATTERN: SUMPRODUCT with date range + status filters. Cross-references Setup!B10 (burden rate), Setup!B9 (std hours), Setup!B8 (billable rate).

## Tab 3: Expenses (14 baseline categories)
- COGS Tools: $6,429/mo
- Rent: $3,813/mo
- Insurance: $794/mo
- Debt Service (BDC + AMEX + LOC): $3,057/mo
- Marketing: $1,869/mo
- SGA Tools: $4,542/mo
- Professional (Legal, Accounting): $4,980/mo
- Facilities: $367/mo
- Recruiting/HR: $7,183/mo
- Bank Fees: $3,195/mo
- Sales: $2,260/mo
- Taxes: $1,867/mo
- Other: $626/mo
**Baseline Total: ~$40,982/mo**

Planned Changes section (Couplier, Gitbook — no amounts yet)
Monthly Expense Totals: People Cost + Non-People Baseline + Planned Changes = TOTAL EXPENSES

FORMULA PATTERN: IF(AND(month>=start, OR(end=0, month<=end)), amount, 0)

## Tab 4: Pipeline (22 deals)
Key deals (Won):
- Rapido Train: $150K CAD, 5 months (May start)
- MA Matting: $229.5K (USD $170K × 1.35), 5 months
- Litetronic: $189K (USD $140K × 1.35), 4 months
- WT Falrye: $86.4K (USD $64K × 1.35), 3 months
- Federal Supply (IP): $60.75K, 4 months
- True Terpenes: $116.7K, 6 months
- Fumex: $63.6K, 3 months
- Jendco: $58.2K, 3 months
- TA Appliance retainer: $10,500/mo, 9 months
- Clarius retainer: $8,100/mo, 6 months

Negotiation stage:
- Vitamin Shop: $150K CAD, 5 months (75% prob)
- Perfect Sports: $150K CAD, 5 months (75% prob)

Lost: ID+A ($114.75K)

Pipeline distributes deal value / duration months into monthly revenue columns.

## Tab 5: Revenue
Auto-calculated from Pipeline:
- Booked Projects (Won deals)
- Booked Retainers (Won retainers)
- Pipeline Projects (probability-weighted)
- Other Revenue (manual)
- Forecast Revenue = sum of above
- Required Revenue (for target profit)
- Gap to Required
- Coverage %

## Tab 6: Plan (Forward P&L)
Auto-calculated management P&L:
- Revenue (from Revenue tab)
- Delivery Team cost (billable staff from People)
- Payroll Burden
- COGS Tools
- GROSS PROFIT / Gross Margin %
- Operational Team (non-billable staff)
- Non-People OpEx
- TOTAL COSTS
- PRETAX PROFIT / Pretax Margin %

KPIs:
- LER (Gross Profit / Delivery Labor)
- LER Status
- Salary Cap (at target profit)
- Revenue Needed (10% and 15%)
- Revenue Gap
- Pipeline Coverage %
- Revenue per Billable FTE / Total FTE
- Overhead Ratio
- Expense Ratios vs benchmarks (Payroll 15-20%, Marketing 3-5%, Rent 2-4%, Software 1-3%, Professional 2-4%, Office 1-2%, Total Below-GP <30%)

## Tab 7: Cash
- Opening Cash: $200,000 (Jan 2026 input)
- Cash In: Collections (Revenue adj. for DSO) + New Deal Deposits + Other
- Cash Out: Payroll + Burden + Contractors + Non-People Expenses + Tax Reserve + Owner Distributions
- Net Cash Flow / Closing Cash
- Cash Health: Monthly OpEx, Core Capital Target, Core Capital Status, Months of Runway

## Tab 8: Scorecard
KPI dashboard for selected month (default: month 4/April):
- LER vs target 2.0
- Pretax Profit % vs target 10%
- Salary Cap Status vs "Under Cap"
- Gross Margin % vs target 60%
- Closing Cash, Core Capital Status vs "Healthy"
- Months of Runway vs target 2
- Forecast Revenue, Pipeline Coverage vs 100%
- Revenue Gap to 10% vs 0
- Revenue per FTE metrics
- Overhead Ratio vs 30%
- Capacity Utilization vs 80%
- Crabtree Checks: Profit >= 10%?, LER >= 1.80?, Core Capital Met?, Ready to Hire?

## Tab 9: CFO Roadmap
Status column shows what exists vs "TO BUILD":

Already in workbook: P&L, Cash Forecast, LER, Salary Cap, Expense Ratios, Pipeline Coverage
Native in tools: Productive (utilization, project margins, EBR, capacity) + QB (AR, AP, Balance Sheet)

TO BUILD:
- 13-Week Rolling Cash Forecast (separate tab)
- DSO Trend (QB + Custom)
- Profit per Principal-Hour (Productive + Custom)
- Project Type Profitability (Productive + Custom)
- Leverage Ratio by Project (Productive + Custom)
- Client Concentration Report (QB or Productive)
- Client Satisfaction/NPS (Custom survey)
- Repeat Client Rate (Custom)
- Bookings vs Target (HubSpot/CRM + Plan)
- Engagement Experience Survey (Custom)
- Working Capital Trend (QB + Custom)
- Rolling 12-Month P&L (QB + Custom)
- Business Valuation Estimate (Annual)

## Known Issues
1. Formula cells return None — model never recalculated in actual Excel
2. Rahul's end date set to March 2026 — needs update
3. Owner (CEO) row has no monthly cost (references Setup wage but may be broken)
4. Some row reference misalignment (AI noted "AI did something weird here")
5. Pipeline tab has mixed currency (CAD + USD × 1.35) — conversion handled in notes, not formulas
6. No invoice schedule tab (Mike mentioned wanting this)
7. No actuals vs budget comparison
8. No 13-week cash flow (only monthly)
9. Blended rate $180/hr may not reflect reality per Mike ("our rates are not $50")
