# Quarter Close ALM Mini System (IFRS-style Controls + KPI Outputs)

A mini quarter-close ALM pipeline that produces model-ready outputs and KPIs with an **auditable, disciplined controls environment** (run manifests, data-quality gates, and quarterly change tickets).  
Built to mirror operations + reporting workflows where traceability and repeatability matter.

---

## AXIS alignment (honest)

This project does **not** run or configure GGY AXIS. It is an **AXIS-like quarter-close ALM mini-system** that mirrors the workflow *around* AXIS:

- **Asset inventory extract** → AXIS asset file analog  
- **Economic assumption inputs** (yield curves / spreads) → AXIS assumption input analog  
- **Controls + traceability** (DQ gates, manifests, change tickets) → disciplined controls environment expectations  
- **Asset-only UAT evidence** → aligns to “execute asset-only user testing” language

See: `AXIS_MAPPING.md` and `/user_testing/`.

---

## Where to look (fast)

- AXIS mapping: `AXIS_MAPPING.md`
- Asset-only UAT: `user_testing/test_cases.xlsx` + `user_testing/uat_summary.md`
- Core notebook: `notebooks/quarter_close_alm.ipynb`
- Controls evidence (close pack): `close_pack/controls/`
- Outputs: `data/outputs/`

---

## Notebook → Mini “System” (what makes this production-like)

This is not just an analysis notebook. The notebook is structured as a repeatable **mini-system** that resembles how quarter-close ALM reporting support is executed:

- **Standardized inputs/outputs:** predictable folder paths and naming conventions for quarter-close artifacts  
- **Config-driven runs:** parameters (paths, run settings, and assumptions selection) are set once and reused consistently  
- **Deterministic execution:** running top-to-bottom reproduces the same outputs given the same inputs  
- **Controls-first workflow:** every run produces an audit trail (manifests, DQ gates, and change tickets)  
- **Run packaging mindset:** outputs + controls evidence are organized as a “close pack” to support review and sign-off

Explainable to auditors and usable by operations: every run leaves behind reproducible evidence.


---

## Quick Start (Google Colab)

**Option A — Run in Colab (recommended):**
1. Open the notebook: `notebooks/quarter_close_alm.ipynb`
2. Update the project path to your Drive folder (example: `quarter_close_alm`)
3. Run all cells top-to-bottom

**What you’ll get:**
- KPI outputs in `data/outputs/` (or your outputs folder)
- Controls evidence in `close_pack/controls/`


> [Open In Colab](https://colab.research.google.com/drive/11yJ9f0l_RgMHM2K0KXTIVoVwAXaqeDVn)

---

## Disciplined Controls Environment (Audit Trail)

Each run produces immutable controls evidence for auditability:

- **Run Manifest (JSON):** `close_pack/controls/run_manifest.json`  
  Includes `run_id`, `timestamp_utc`, `git_commit` (if available), `config_hash`, and **SHA256 checksums** for all input/output files.

- **Run Manifest (XLSX):** `close_pack/controls/run_manifest.xlsx`  
  Human-readable run summary (meta + config + file checksums).

- **Data Quality Gate Report (one page):** `close_pack/controls/dq_gate_report.xlsx`  
  “Controls Summary” includes:
  - required columns PASS/FAIL  
  - null counts  
  - duplicate checks  
  - out-of-range checks  
  - exceptions count  
  - sign-off field

- **Quarterly Change Ticket:** `close_pack/controls/change_ticket_<QUARTER>.md`  
  Captures what changed (curves/spreads/policy), why, expected impact, testing performed, and approvals (simulated OK).

You can reproduce any run, verify file integrity, and show a clear control framework—exactly what “disciplined controls environment” implies.

---

## Outputs & KPIs (What this project produces)

Typical outputs include:
- **Asset inventory / roll-forward extracts**
- **Economic assumptions snapshots** (curves/spreads)
- **Reinvestment strategy outputs** (if applicable)
- **Quarter-close KPI tables** (e.g., Assets, Surplus, attribution drivers)

Primary output location:
- `data/outputs/` 

---

## How the Pipeline Works (High-level)

1. **Load inputs** (positions, assumptions, mappings)
2. **Validate inputs** (required columns + data quality gates)
3. **Transform / build model-ready tables**
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

