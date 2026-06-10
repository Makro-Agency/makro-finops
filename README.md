# makro-finops

Financial operations data pipeline for Makro Agency. Pulls from QuickBooks, Atio CRM, Teamwork, and Plaid. Computes KPIs. Pushes to Google Sheets model. Delivers reports and alerts.

## Architecture

```
Source Systems → Collection (MCP/API) → YAML Snapshots (Git) → Computation (Python) → Outputs
                                                                                      ├── Google Sheets (live model)
                                                                                      ├── CEO Dashboard (HTML)
                                                                                      ├── Slack Alerts
                                                                                      ├── Daily Cash Email
                                                                                      └── Monthly Close Report
```

## Directory Structure

```
makro-finops/
├── config/              # Thresholds, source definitions, cadences, FX rates
│   ├── thresholds.yaml  # Green/Yellow/Red bands for all metrics
│   ├── sources.yaml     # Data source registry (QB, CRM, Teamwork, Plaid)
│   ├── cadences.yaml    # Daily/weekly/monthly/quarterly rhythm definitions
│   └── fx-rates.yaml    # Currency conversion rates
├── snapshots/           # Raw and normalized data pulls (YAML, timestamped)
│   ├── raw/             # Direct API/MCP output
│   └── normalized/      # After transformation (currency, dates, categories)
├── computed/            # Derived metrics and analysis
│   ├── daily/           # Cash position, project burns
│   ├── weekly/          # Ops snapshot metrics, 2-week forecast, compliance
│   ├── monthly/         # P&L, salary cap, client profitability, 13-week forecast
│   └── alerts/          # Active threshold breaches
├── scripts/             # Python extractors, transformers, metric engine
├── model/               # Financial model (Google Sheets link + archived Excel)
├── reports/             # Generated HTML reports
├── tests/               # pytest for metric calculations
└── docs/                # Context docs, architecture decisions
```

## Key Metrics

| Metric | Target | Floor | Source |
|--------|--------|-------|--------|
| Pretax Profit % | 15% | 10% | Crabtree |
| LER | 2.0 | 1.80 | Crabtree |
| Gross Margin % | 60% | 50% | SPI Benchmark |
| DSO | 30 days | 45 days | Industry |
| Cash Runway | 3 months | 2 months | Crabtree |
| Utilization (blended) | 70%+ | 60% | SPI Benchmark |
| Client Concentration | <20% top 1 | <25% | Risk standard |

## Cadences

- **Daily:** Cash email (9 AM), project burn check (9:30 AM), AR scan (10 AM)
- **Weekly:** Ops snapshot (Mon 10 AM), 2-week cash forecast, time compliance
- **Monthly:** P&L close (by 5th), full 13-week forecast, utilization, expense variance, client profitability, salary cap
- **Quarterly:** 3-scenario reforecast, software audit, client concentration, tax reserve

## Setup

1. Install MCP servers: QuickBooks, Google Sheets, Attio CRM
2. Configure credentials in `.env` (not committed)
3. Run `python scripts/validate_sources.py` to verify connections
4. See `reports/ops_financial_model_review.html` for full architecture docs
