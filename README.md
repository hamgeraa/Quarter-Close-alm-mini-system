## Quarter-Close-alm-mini-system
Built a mini system that simulates an insurance quarter-close ALM workflow:
- Ingests asset holdings + economic assumptions (yield curve + credit spreads)
- Generates AXIS-like input files
- Runs base vs. scenario valuation (MVP proxy)
- Produces a KPI dashboard, exceptions, and surplus attribution
- Packages everything into a quarter-close deliverable pack with controls evidence

---

## Business Problem
Quarter-close reporting (IFRS / PBR / ALM) depends on runs that are:
- repeatable (same inputs → same outputs)
- controlled (validated data, documented assumptions)
- explainable (“what changed and why?”)
This project demonstrates that discipline end-to-end: controlled inputs → run → reconciliation → attribution → close pack.

---

## Inputs
Holdings (asset inventory): synthetic but intentionally “messy” (real-world style issues)

Economic assumptions:
- Yield curve (tenor → rate)
- Credit spreads (rating → spread bps)

Scenario shocks (from config): rate shock bps + spread shock bps
Reinvestment policy rules: liquidity reserve, max below-IG, duration target


---

## Method Overview (Quarter-Close Pipeline)

1. Setup + MVP Run
- Build AXIS-like input files
- Run base + scenario valuation (proxy)
- Generate KPI dashboard + reconciliation folder outputs
  
2. Controls + Data Validation
- Required-column checks
- Numeric sanity checks
- Exception logging (what’s wrong + how to fix)

3. Assumption Governance (Quarterly Updates)
- Version assumptions by quarter (prior vs current)
- Diff report in bps by tenor (curve) + rating (spreads)
- Reinvestment Strategy (Investment Inputs)

4. Apply policy rules
- Generate allocation plan by sector/rating/duration band
- Output investment inputs (CSV + Excel)
- Attribution + Reconciliation (the stand-out)

5. Explain surplus movement via:
- rate impact
- spread impact
- carry proxy
- residual (ties-out)
Stakeholder-friendly attribution table + dashboard sheet

6. Close Pack (Recruiter-ready bundle)
- Executive summary (1 page)
- Controls evidence checklist + run manifest
- Pack outputs into a shareable folder/ZIP


## Screenshots
<img width="336" height="93" alt="KPI" src="https://github.com/user-attachments/assets/993caa0e-eb4a-4248-8a12-cb81fbcb6c9c" />
<img width="201" height="146" alt="Screenshot 2025-12-21 at 7 43 10 PM" src="https://github.com/user-attachments/assets/d0c2146b-ab2a-420b-98f3-6cc6d224fb16" />
<img width="967" height="496" alt="Screenshot 2025-12-21 at 7 44 20 PM" src="https://github.com/user-attachments/assets/9dd54ae2-dce0-4b39-b36a-c907d6a5a8f1" />

