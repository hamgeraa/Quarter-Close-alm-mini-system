TL;DR

Built a recruiter-ready mini system that simulates an insurance quarter-close ALM workflow:

Ingests asset holdings + economic assumptions (yield curve + credit spreads)

Generates AXIS-like input files

Runs base vs. scenario valuation (MVP proxy)

Produces a KPI dashboard, exceptions, and surplus attribution

Packages everything into a quarter-close deliverable pack with controls evidence

Business Problem

Quarter-close reporting (IFRS / PBR / ALM) depends on runs that are:

repeatable (same inputs → same outputs)

controlled (validated data, documented assumptions)

explainable (“what changed and why?”)

This project demonstrates that discipline end-to-end: controlled inputs → run → reconciliation → attribution → close pack.

Inputs

Holdings (asset inventory): synthetic but intentionally “messy” (real-world style issues)

Economic assumptions:

Yield curve (tenor → rate)

Credit spreads (rating → spread bps)

Scenario shocks (from config): rate shock bps + spread shock bps

Reinvestment policy rules: liquidity reserve, max below-IG, duration target

Method Overview (Quarter-Close Pipeline)

Setup + MVP Run

Build AXIS-like input files

Run base + scenario valuation (proxy)

Generate KPI dashboard + reconciliation folder outputs

Controls + Data Validation

Required-column checks

Numeric sanity checks

Exception logging (what’s wrong + how to fix)

Assumption Governance (Quarterly Updates)

Version assumptions by quarter (prior vs current)

Diff report in bps by tenor (curve) + rating (spreads)

Reinvestment Strategy (Investment Inputs)

Apply policy rules

Generate allocation plan by sector/rating/duration band

Output investment inputs (CSV + Excel)

Attribution + Reconciliation (the stand-out)

Explain surplus movement via:

rate impact

spread impact

carry proxy

residual (ties-out)

Stakeholder-friendly attribution table + dashboard sheet

Close Pack (Recruiter-ready bundle)

Executive summary (1 page)

Controls evidence checklist + run manifest

Pack outputs into a shareable folder/ZIP

Key Outputs / Artifacts

Dashboard & reporting

kpi_dashboard.xlsx — Summary KPIs + Exceptions + Attribution

assumptions_diff_report.xlsx — quarterly assumption changes (bps)

reinvestment_inputs.xlsx — reinvest summary + plan

AXIS-like inputs (axis_like_inputs/)

asset_inventory.csv

econ_yield_curve_base.csv, econ_yield_curve_shocked.csv

credit_spreads_base.csv, credit_spreads_shocked.csv

reinvestment_plan.csv, reinvestment_summary.csv

Reconciliation pack (reconciliation_pack/)

kpis.csv

exceptions_assets.csv

attribution_summary.csv

Close pack

executive_summary.md

controls_evidence_checklist.csv

run_manifest.csv

quarter_close_pack_YYYYQ#.zip (optional / available on request)

## Screenshots
<img width="336" height="93" alt="KPI" src="https://github.com/user-attachments/assets/993caa0e-eb4a-4248-8a12-cb81fbcb6c9c" />
<img width="201" height="146" alt="Screenshot 2025-12-21 at 7 43 10 PM" src="https://github.com/user-attachments/assets/d0c2146b-ab2a-420b-98f3-6cc6d224fb16" />
<img width="967" height="496" alt="Screenshot 2025-12-21 at 7 44 20 PM" src="https://github.com/user-attachments/assets/9dd54ae2-dce0-4b39-b36a-c907d6a5a8f1" />

