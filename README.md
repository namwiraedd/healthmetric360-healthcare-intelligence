# HealthMetric 360 | Healthcare Intelligence MVP

**From healthcare data to better decisions.**

A reproducible healthcare analytics portfolio project demonstrating synthetic data engineering, Power BI semantic modelling, predictive machine learning and management decision support.

> **Important:** Every record is synthetic. This project is not a clinical decision-support device and its model outputs must not be used for patient care.

## What is included
- 4,200 synthetic patient profiles and 16,000 encounter records across 24 months.
- Department-level operational and financial performance.
- Monthly medicine inventory and demand data.
- ML model for missed-follow-up risk (classification).
- Monthly patient-volume forecast (regression with lag features and chronological holdout).
- Medicine demand estimator (regression).
- Scored CSVs, evaluation metrics and a rule-based management action register.
- Power BI table relationships, starter DAX measures and client dashboard specification.

## Quick start
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python src/generate_data.py
python src/train_models.py
python src/build_decision_register.py
```

The generator recreates the raw synthetic data. The training script writes model artifacts to `models/`, scored tables to `data/processed/`, and metrics to `reports/model_metrics.json`.

## Power BI
1. Open Power BI Desktop → Get Data → Text/CSV.
2. Import the CSV files listed in `powerbi/model_relationships.md`.
3. Set date and numeric data types; use `encounter_id` as the encounter key.
4. Create a Date dimension and relationships as documented.
5. Add measures from `powerbi/measures.dax`.
6. Build the six pages in `docs/dashboard_specification.md`.
7. For a clean client demo, hide raw IDs and use aggregate visuals by default.

The repository contains Power BI-ready source tables and specifications, not a compiled `.pbix` file. Build and save the `.pbix` in Power BI Desktop after importing the data.

## Model overview and validation
| Use case | Model | Evaluation |
|---|---|---|
| Follow-up risk | Random Forest classifier | ROC-AUC, precision, recall, F1 |
| Patient volume | Random Forest regressor with lag features | MAE, RMSE, R² on final six months |
| Medicine demand | Random Forest regressor | MAE, RMSE, R² on held-out rows |

The follow-up outcome is simulated from synthetic risk factors. The demand model uses a random holdout for this demo; a production-grade time-series validation design should use chronological splits. Metrics are not evidence of real-world clinical performance.

## Suggested GitHub repository description
Healthcare analytics MVP with synthetic hospital data, Power BI-ready datasets, Python machine-learning models, forecasting, operational KPIs and management decision support.

## Suggested topics
`healthcare-analytics` `power-bi` `python` `machine-learning` `health-informatics` `predictive-analytics` `business-intelligence` `data-science`

## Production roadmap
1. Validate source-system data definitions and completeness.
2. Implement secure ingestion, access controls and audit trails.
3. Validate models on representative, appropriately governed real-world data.
4. Conduct subgroup performance and bias assessment.
5. Establish human review, model monitoring and change control.
6. Complete privacy, security, legal and regulatory assessments in each deployment jurisdiction.
