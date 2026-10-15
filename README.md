# SCSE3040 Practical 06 — Experiment Tracking with MLflow

This repository contains the P06 Jupyter notebook for tracking delivery-time prediction experiments with MLflow, comparing runs through the tracking database, logging a Linear Regression baseline, and recording a Decision Tree sweep.

## Contents

- `P06.ipynb` — course walkthrough with T1, T2, and T3 implemented.
- `data/delivery_times.csv` — the course's 600-row dataset.
- `work/` — MLflow's SQLite tracking database is created here when the notebook runs.
- `mlartifacts/` — model artifacts are created here during notebook execution and are intentionally git-ignored.

## Run locally

Run commands from the repository root.

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m notebook P06.ipynb
```

macOS/Linux:

```bash
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m notebook P06.ipynb
```

Run all cells from top to bottom. Once the notebook has logged runs, start the UI using the exact database URI printed by the notebook, for example:

```bash
python -m mlflow ui --backend-store-uri sqlite:///./work/mlflow.db --port 5000
```

Open http://127.0.0.1:5000 and select the `delivery-time` experiment. Capture your own screenshot of the run table with the `mae_minutes` column visible and at least six runs. Do not submit a placeholder image; the screenshot must show runs created by your execution.

## Submission checklist

- Execute every notebook cell and save it with outputs visible.
- Confirm the `linear-baseline` run exists.
- Confirm T2 finds the lowest MAE using `mlflow.search_runs`.
- Confirm three runs are tagged `family=tree`, with depths 2, 4, and 6.
- Add the real MLflow UI screenshot to your course submission.
- Verify the notebook self-check passes.

This implementation follows the official SCSE3040 P06 lab handout.
