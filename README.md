# Market Sentiment and Return Analysis

This repository examines whether consumer and investor sentiment help explain short-term stock market returns and whether sentiment matters differently across firm types in a panel setting. The project combines monthly macro sentiment data with a firm-year panel to focus on the analysis rather than the course scaffolding that produced it.

## What To Look At First

- [Final monthly panel](data/final/analysis_panel.csv) combining Michigan consumer sentiment, AAII investor sentiment, and Fama-French-style market factors.
- [Firm-panel dataset](data/final/m3v2_firm_panel.csv) used for fixed-effects and difference-in-differences models.
- [Interactive M3v2 dashboard](results/reports/M3v2_interactive_dashboard.html) for model comparison and coefficient exploration.
- [M3v2 interpretation](results/reports/M3v2_interpretation.md) for the cleanest plain-language summary of the panel results.

## Project Summary

The core research question is whether sentiment is predictive, contrarian, or mostly uninformative once standard controls are included. The work evolved into two related analyses:

- A monthly time-series panel with Michigan sentiment, AAII sentiment, and Ken French factors.
- A firm-year panel built from Compustat-style data to test fixed effects, exposure interactions, and event-style specifications.

The strongest public-facing outputs are the data products, regression tables, and figures in `data/final/` and `results/`.

## Key Findings

- In pooled monthly models, lagged sentiment is generally weak on its own once controls are included.
- In the firm panel, sentiment matters more through exposure differences, especially for smaller firms.
- The most useful artifacts for a portfolio or resume are the cleaned datasets, coefficient tables, event-study figure, and dashboard rather than the assignment writeups.

## Repository Layout

- `code/` contains the scripts that build the datasets, tables, figures, and dashboard.
- `data/raw/` stores source files.
- `data/processed/` stores cleaned intermediate datasets.
- `data/final/` stores the analysis-ready outputs.
- `results/figures/` stores the charts and event-study visuals.
- `results/tables/` stores regression and diagnostic tables.
- `results/reports/` stores the polished summaries and dashboard.
- `archive/` stores the older milestone and submission-era files that are kept for completeness but are no longer the main story.

## Reproduce The Main Outputs

Install dependencies first:

```bash
pip install -r requirements.txt
```

Then regenerate the monthly sentiment pipeline and panel outputs:

```bash
python code/run_all_fetch_scripts.py
python code/merge_final_panel.py
python code/visualize_final_panel.py
```

To rebuild the firm-panel analysis and dashboard:

```bash
python code/capstone_models.py
python code/create_m3v2_interactive_dashboard.py
```

If you want a quick visual overview, open these outputs in your browser:

- [M3v2 dashboard](results/reports/M3v2_interactive_dashboard.html)
- [Time-series dashboard](results/reports/M2_interactive_dashboard_v2.html)

## Selected Outputs

- [Monthly analysis panel](data/final/analysis_panel.csv)
- [Monthly summary statistics](data/final/summary_statistics.csv)
- [Firm-panel dataset](data/final/m3v2_firm_panel.csv)
- [M3v2 model comparison table](results/tables/m3v2_model_comparison_table.md)
- [Company-controls comparison table](results/tables/m3v2_company_model_comparison_table.md)
- [Event-study figure](results/figures/m3v2_did_event_study.png)
- [Coefficient comparison figure](results/figures/m3v2_coefficient_comparison.png)

## Data Sources

- University of Michigan Survey of Consumers
- AAII Investor Sentiment Survey
- Kenneth R. French Data Library
- Compustat-style firm fundamentals for the panel analysis

## Legacy Files

Older milestone writeups, assignment deliverables, and submission artifacts have been moved to `archive/` so the root of the repository stays focused on the data and analysis.
