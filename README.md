# Customer Churn Prediction & Retention Analytics

A consulting-grade churn analytics project for a telecom subscription business. Predicts which customers will churn, identifies key drivers, and delivers a retention strategy framework.

## Project Overview

| Metric | Value |
|---|---|
| Customers analyzed | 7,043 |
| Churn rate | 26.54% |
| Monthly revenue loss | $139,130 |
| Best model (ROC-AUC) | Logistic Regression — 0.8422 |

## Repository Structure

```
├── data/                          # raw + processed datasets
├── src/
│   ├── download_data.py           # Kaggle dataset download
│   ├── data_processing.py         # missing values, encoding, scaling, outliers
│   ├── ml_pipeline.py             # LR, RF, XGBoost + CV + ROC + confusion matrices
│   ├── insights.py                # feature importance, SHAP, KMeans, KPI report
│   ├── sql_analysis.py            # SQL query generator
│   ├── generate_report.py         # basic docx report
│   ├── consulting_report.py       # McKinsey-style consulting report
│   └── compute_eda_stats.py       # EDA statistics computation
├── sql/churn_analysis.sql         # 8 production SQL queries
├── outputs/
│   ├── models/                    # 3 trained .pkl models
│   ├── plots/                     # 8 visualization PNGs
│   ├── model_results.json         # model metrics
│   ├── kpi_report.json            # business KPIs
│   └── eda_stats.json             # EDA statistics
├── Telco_Churn_Consulting_Report.docx  # full consulting report (12 sections)
├── run_pipeline.py                # one-command end-to-end pipeline
└── requirements.txt
```

## Quick Start

```bash
pip install -r requirements.txt
python run_pipeline.py
```

This runs the full pipeline: download → process → train models → generate insights → SQL → report.

## ML Models

| Model | ROC-AUC | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|---|
| Logistic Regression | **0.8422** | 0.8062 | 0.6593 | 0.5588 | 0.6049 |
| XGBoost | 0.8326 | 0.7935 | 0.6309 | 0.5348 | 0.5789 |
| Random Forest | 0.8259 | 0.7921 | 0.6355 | 0.5080 | 0.5646 |

## Key Findings

- **Month-to-month contracts** churn at 42.7% — 15x higher than two-year contracts
- **Electronic check** payment correlates with 45.3% churn — 3x auto-pay methods
- **First 6 months** is the highest-risk period at 53.3% churn
- **Fiber optic** subscribers churn at 41.9% vs 19.0% for DSL
- A **high-risk segment** of 876 customers (12.4% of base) has a 70.5% churn rate

## Reports

- `Telco_Churn_Consulting_Report.docx` — 12-section consulting-grade report with executive summary, EDA, ML models, SHAP analysis, customer segmentation, SQL queries, 8 business insights, retention strategy, and deployment roadmap.

## Dataset

IBM Telco Customer Churn dataset (Kaggle). 7,043 customers, 21 features covering demographics, account information, services, and billing.

## License

MIT
