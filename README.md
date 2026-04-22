# HAVI QSR Demand Forecasting — Hackathon 2026 2nd Place

Team repository for the **HAVI / NIU Quick Service Restaurant (QSR) Demand Forecasting Challenge**: predict daily item demand from history, calendar, weather, and promotions, then submit forecasts for the official holdout window.

See [`CONTEXT.txt`](CONTEXT.txt) for shared project assumptions, strategy, and non‑negotiables (no leakage, time-based validation, optimize for wMAPE).

---

## Objective

Forecast **`quantity`** for every **restaurant × menu item × day** in the holdout period:

| Item | Detail |
|------|--------|
| **Holdout dates** | **2025-10-01** through **2025-12-31** |
| **Submission rows** | **69,000** (92 days × 15 restaurants × 50 menu items) |
| **Metric** | **wMAPE** (weighted mean absolute percentage error). **Lower is better.** |
| **Scoring note** | Confirm the exact wMAPE definition with official rules; locally we track both a **global** wMAPE (Σ\|error\| / Σ actual) and notebook-style item-volume weighting where useful. |

### Submission file format

Columns (in order):

`date` · `restaurant_id` · `menu_item_id` · `predicted_quantity`

Example artifacts in this repo: `submission.csv` (root), `data/submissions/qsr_forecast_Anthony_model_submission.csv`.

---

## Data

- **Full history (typical workflow):** `qsr_demand_dataset.csv` — ~**1.37M** daily rows from **2021–2025**, **15** restaurants, **50** menu items, Midwest locations.  
  Each row is one day for one restaurant–item; features include calendar, weather, holidays, events, and promotions (see `CONTEXT.txt` for column groups).

- **Pre-split CSVs (optional / teammate workflow):** under `data/`:

  | Path | Role |
  |------|------|
  | `data/training/train_set.csv` | Training split |
  | `data/validation/val_set.csv` | Validation split |
  | `data/test/test_set.csv` | Test / holdout features |
  | `data/submissions/` | Example or teammate submission files |

The raw competition file is large; keep it out of git if you use Git LFS or local-only copies—check your remote policy.

---

## Repository layout

| Path | Purpose |
|------|---------|
| `CONTEXT.txt` | Hackathon context, dataset summary, team process, rules for modeling |
| `EDA.ipynb` | Exploratory analysis |
| `qsr_forecast.ipynb` | Main Python forecasting pipeline (baseline → features → LightGBM, time-based validation) |
| `qsr_forecast (1).ipynb` | Alternate / evolved notebook (e.g. Colab-oriented workflow, blended baseline + GBM) |
| `mario_eda.qmd` | Quarto EDA / narrative |
| `charts/` | Plots and figures |
| `models/` | Saved models (if committed) |
| `requirements.txt` | Python dependencies |
| `renv.lock`, `renv/`, `.Rprofile` | **R** reproducible environment ([renv](https://rstudio.github.io/renv/)) |

---

## Setup

### Python

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Core stack: **pandas**, **numpy**, **LightGBM**, **scikit-learn**, **matplotlib**, **seaborn**, **ipykernel** (see `requirements.txt` for versions).

### R

From the repo root (with R installed):

```r
renv::restore()
```

Uses `renv.lock` for pinned packages.

---

## Modeling principles (from `CONTEXT.txt`)

1. **No future leakage** in features.
2. **Time-based validation only** (e.g. hold out **September 2025** before forecasting Oct–Dec).
3. **Optimize for wMAPE**, not generic point-accuracy alone.
4. Prefer **interpretable, reproducible** pipelines over fragile complexity.
5. Keep outputs **interoperable** (Python ↔ R) where both are used.

Typical flow: strong baseline → time-aware features (lags, rolls, calendar, weather, events) → **LightGBM** (or similar) → validate on calendar holdout → retrain on all pre-forecast history → generate **69k** submission rows.

---

## License

[`LICENSE`](LICENSE) — MIT (see file for copyright holder).
