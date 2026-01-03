# Quarter-Close ALM Mini System (IFRS-Style Controls + KPI Outputs)

A quarter-close ALM **mini-system** that produces model-ready outputs and KPI tables within an **auditable, disciplined controls environment**.  
Designed to mirror insurance ALM operations where **traceability, repeatability, and explainable results** are required for quarterly reporting.

**What this demonstrates (in Transamerica language):**
- Produce **asset inventory + economic assumption inputs** (AXIS-like analogs)
- Generate **KPI outputs** for operations + reporting
- Enforce **controls** (DQ gates, run manifests, quarterly change tickets)
- Provide **asset-only UAT evidence** and reconciliation-ready outputs

---

## AXIS Alignment

This project does **not** run or configure GGY AXIS. Instead, it mirrors the quarter-close workflow *around* AXIS to demonstrate operational readiness:

- **Asset inventory extract** → AXIS asset file **analog**
- **Economic assumptions** (yield curve / credit spreads) → AXIS assumption input **analog**
- **Controls evidence** (DQ gates, manifests, change tickets) → disciplined controls expectations
- **Asset-only UAT evidence** → aligns with “execute asset-only user testing” responsibilities

See:
- `AXIS_MAPPING.md`
- `/user_testing/`

---

## Where to Look

- **AXIS mapping:** `AXIS_MAPPING.md`  
- **Asset-only UAT:** `user_testing/test_cases.xlsx` + `user_testing/uat_summary.md`  
- **Core workflow:** `notebooks/quarter_close_alm.ipynb`  
- **Controls evidence (“close pack”):** `close_pack/controls/`  
- **Outputs:** `data/outputs/`

---

## Notebook → Mini System 

This is not a one-off analysis. The workflow is structured like a repeatable quarter-close run:

- **Standardized inputs/outputs:** predictable folder structure + naming conventions for close artifacts  
- **Config-driven runs:** run parameters set once and reused consistently  
- **Deterministic execution:** same inputs → same outputs (reproducible results)  
- **Controls-first:** every run produces an audit trail (manifests, DQ gates, change ticket)  
- **Close-pack packaging:** outputs + controls evidence organized for review and sign-off  

Result: explainable to reviewers/auditors and usable by operations teams.

---

## Quick Start (Google Colab)

**Option A — Run in Colab (recommended):**
1. Open: `notebooks/quarter_close_alm.ipynb`  
2. Update the project path to your Drive folder (example: `quarter_close_alm`)  
3. Run all cells top-to-bottom  

**You will get:**
- KPI outputs in `data/outputs/`  
- Controls evidence in `close_pack/controls/`  

Open in Colab: `https://colab.research.google.com/drive/11yJ9f0l_RgMHM2K0KXTIVoVwAXaqeDVn`

---

## Disciplined Controls Environment (Audit Trail)

Each run generates immutable controls artifacts to support auditability and quarter-close governance:

- **Run Manifest (JSON):** `close_pack/controls/run_manifest.json`  
  Includes `run_id`, `timestamp_utc`, `git_commit` (if available), `config_hash`, and **SHA-256 checksums** for all input/output files.

- **Run Manifest (XLSX):** `close_pack/controls/run_manifest.xlsx`  
  Human-readable summary (run meta + configuration + file checksums).

- **Data Quality Gate Report (one page):** `close_pack/controls/dq_gate_report.xlsx`  
  Controls Summary includes:
  - required columns PASS/FAIL  
  - null counts  
  - duplicate checks  
  - out-of-range checks  
  - exceptions count  
  - sign-off field  

- **Quarterly Change Ticket:** `close_pack/controls/change_ticket_<QUARTER>.md`  
  Captures: what changed (curve/spreads/policy), why, expected impact, testing performed, and approvals (simulated acceptable).

This framework supports run reproducibility, file integrity verification, and controlled quarter-close change documentation.

---

## Outputs & KPIs

Typical outputs include:
- **Asset inventory / roll-forward extracts**
- **Economic assumptions snapshots** (yield curve + credit spreads)
- **Reinvestment strategy outputs** (if applicable)
- **Quarter-close KPI tables** (e.g., Assets, Surplus, attribution drivers)

Primary output location:
- `data/outputs/`

---

## Pipeline 

1. **Load inputs** (positions, assumptions, mappings)  
2. **Validate inputs** (required columns + DQ gates)  
3. **Transform into model-ready tables**  
4. **Compute KPIs / summaries**  
5. **Write outputs** (CSV/XLSX) + **generate controls evidence** in `close_pack/controls/`  

---

## Repository Structure

```text
quarter_close_alm/
  notebooks/
    quarter_close_alm.ipynb
  data/
    inputs/
    outputs/
  close_pack/
    controls/
      run_manifest.json
      run_manifest.xlsx
      dq_gate_report.xlsx
      dq_gate_report.md
      change_ticket_<QUARTER>.md
    results/
  user_testing/
    test_cases.xlsx
    uat_summary.md
  src/
    (optional python modules)
  README.md





## Screenshots
<img width="336" height="93" alt="KPI" src="https://github.com/user-attachments/assets/993caa0e-eb4a-4248-8a12-cb81fbcb6c9c" />
<img width="201" height="146" alt="Screenshot 2025-12-21 at 7 43 10 PM" src="https://github.com/user-attachments/assets/d0c2146b-ab2a-420b-98f3-6cc6d224fb16" />
<img width="967" height="496" alt="Screenshot 2025-12-21 at 7 44 20 PM" src="https://github.com/user-attachments/assets/9dd54ae2-dce0-4b39-b36a-c907d6a5a8f1" />

