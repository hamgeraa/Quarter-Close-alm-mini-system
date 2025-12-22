# Quarter-Close-alm-mini-system
Built a Quarter-Close ALM Mini-System modeled after a real insurance quarterly close workflow . Asset holdings (starting with synthetic, “messy” real-world data) and economic assumptions (yield curve + credit spreads) are ingested, then AXIS-like input files are generated to support Asset & Liability Management analysis. A repeatable base vs. scenario valuation (MVP proxy) is run and results are summarized in a stakeholder-friendly KPI dashboard showing assets, liabilities, and surplus.

To reflect a disciplined close process, controls and data validation are included: required-column checks, numeric sanity checks, and an exceptions report that highlights data quality issues so they can be corrected before results are finalized. Assumption governance is demonstrated by versioning assumptions by quarter and producing a basis-point diff report (by tenor for the yield curve and by rating for credit spreads), making quarterly assumption changes transparent and explainable.

On the investment side, a simplified reinvestment strategy is produced using policy rules (liquidity reserve, maximum below-investment-grade exposure, and a duration target). The strategy outputs a reinvestment plan and summary in CSV and Excel formats. The “stand-out” reconciliation component is implemented through attribution, breaking surplus movement into rate impact, spread impact, a carry proxy, and residual so the core close question can be answered: “Why did surplus change?”

## Screenshots
<img width="336" height="93" alt="KPI" src="https://github.com/user-attachments/assets/993caa0e-eb4a-4248-8a12-cb81fbcb6c9c" />
<img width="201" height="146" alt="Screenshot 2025-12-21 at 7 43 10 PM" src="https://github.com/user-attachments/assets/d0c2146b-ab2a-420b-98f3-6cc6d224fb16" />
<img width="967" height="496" alt="Screenshot 2025-12-21 at 7 44 20 PM" src="https://github.com/user-attachments/assets/9dd54ae2-dce0-4b39-b36a-c907d6a5a8f1" />

