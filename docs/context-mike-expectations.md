# Mike's Expectations from June 8 Call — Ops-Relevant Extraction

## The Apex Mandate
"Profit is the first metric... if one thing, if we did it right and we just did that one thing, we'll be successful."
"Build the walls before the furniture." — Don't build dashboards/automation before knowing core numbers.

## 4 CEO Questions (Must Be Answerable in <5 min)
1. Are we good?
2. Did we hit the sales target?
3. Does our revenue cover our team?
4. Are we on margin?

## Explicit Expectations for Ops
1. **Profit visibility at any time** — not monthly, not quarterly, at any moment
2. **Financial model as living system** — the Excel must be maintained, fed real data, produce reliable outputs
3. **Deterministic outputs** — same run = same result. Script-based, not generative AI guessing
4. **Redact sensitive data** when using AI (client names, invoice numbers) — Microsoft Presidio package mentioned
5. **No manual spreadsheet work** — "should be manual-ish" at most. Inputs maintained, calculations automated
6. **Every KPI connects to profit** — don't track standalone vanity metrics
7. **Revenue = bookings + invoice schedule** — predictable. AR is the nightmare (delays = cash flow hit)
8. **Actuals vs budgeted** — import from QuickBooks at month-end, compare to forecast
9. **13-week cash flow forecast** — rolling, weekly refresh on 2-week horizon, full 13 at monthly close
10. **Rhythms are non-negotiable** — daily cash, weekly ops snapshot, monthly close, quarterly reforecast

## Stated Data Source Architecture
- **QuickBooks**: Actuals, expenses, bank balances, AR aging, AP aging. Has custom MCP + custom app already built
- **Atio CRM**: Pipeline, deals, close dates, revenue forecast. AI-first, MCP-ready
- **Teamwork**: Project health, milestones, delivery status, budget burn. Official move from Jira/Smartsheet/Productive
- **Plaid**: Bank starting/ending balances via API endpoint
- **Excel/Google Sheets**: The model itself. Cloud Code reads/writes

## Key Business Context
- Jose = bookkeeper/AR only. Not a finance person. "I have no hopes for him."
- Mike has finance degree, knows how to run this. Problem: "I get things from 0 to 50 and drop them."
- Delegation problem: "I always think I'm the only one that can do it."
- Last 2 years = least profitable in company history. Previous years were profit-disciplined.
- "We might need to fire people within 2 weeks. If the numbers show... can't go against the numbers."
- Salary cap is being exceeded monthly (visible in model)
- 5 new hires added recently — productivity not yet proven
- Clarius may be dropped as client (not profitable, no major projects in 2 years)
- Rashmi and James questioned as cost-effective
- Nick's productivity on B2B Supercharged app questioned

## What Mike Wants to See (Implicit from Discussion)
1. Revenue forecast that's REAL — not fictional. Based on actual bookings + weighted pipeline
2. Cost structure clarity — who costs what, is it justified by revenue they generate
3. Project-level profitability — can we invoice on time? If project delayed, what's the P&L impact?
4. Salary cap enforcement — before any hiring discussion, ops provides cap data
5. Software expense governance — monthly audit, quarterly cleanup (already saving by dropping Jira→Teamwork)
6. Decision support — "if we add developer X from June to September, what happens to model?"
7. Early warning system — "if we didn't hit our sales forecast, I would have been building events instead of something stupid"

## Timeline Commitments
- Rahul reviews Excel model, presents back by Wednesday June 11
- Then: "build an actual plan against it"
- Mike wants ops financial machine operational — implied: weeks, not months
- KPI tracking across all departments starts "week after next" (per Alexis discussion)

## Emotional/Strategic Context
- Mike is frustrated: "how the fuck did we operate without knowing our numbers"
- He's excited about AI making this possible without a finance hire
- He sees this as existential: profit discipline = survival
- "I'm very excited about this. I want to turn things around."
- This is not a nice-to-have project. This is THE project.
