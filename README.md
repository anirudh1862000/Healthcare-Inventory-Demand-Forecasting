# Healthcare Inventory & Demand Forecasting

A healthcare operations analytics project exploring inventory availability, patient flow, staffing, and financial patterns, with a machine-learning workflow to estimate inventory demand.

> **Portfolio focus:** exploratory data analysis, feature engineering, operational metrics, and predictive modeling using Python.

## Business Problem

Healthcare teams need to balance stock availability with demand while monitoring staffing and operating costs. This project brings several operational datasets into an analytical workflow to explore potential inventory shortfalls and replenishment needs.

## Questions Explored

- How does inventory compare with minimum and maximum capacity?
- Where might inventory shortfalls or replenishment needs emerge?
- How do staffing hours and overtime vary?
- What patterns appear in expense categories, patient stays, and procedures?
- Which operational variables may be useful for demand forecasting?

## Workflow

1. **Inspect and prepare data** — review data structures, normalize dates, and combine relevant datasets.
2. **Explore operations** — visualize inventory and capacity, staffing and overtime, expenses, diagnoses and procedures, and patient-stay patterns.
3. **Engineer features** — derive inventory shortfall and replenishment-related fields.
4. **Model demand** — encode categorical variables and build a `GradientBoostingRegressor` workflow.
5. **Review outputs** — use visual analysis and model evaluation to support further investigation.

## Tools & Skills

- **Python:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine learning:** scikit-learn, Gradient Boosting
- **Analytics:** data cleaning, exploratory data analysis (EDA), feature engineering, operational KPI exploration

## Repository Contents

- `supply-chain-in-healthcare.ipynb` — analysis and modeling notebook

## Run the Project

1. Clone or download this repository.
2. Open the notebook in Jupyter or Google Colab.
3. Install the packages used in the notebook: `pandas`, `numpy`, `matplotlib`, `seaborn`, and `scikit-learn`.
4. Update the input file paths to match your environment.
5. Run the notebook from top to bottom.

The notebook references Kaggle input files under `/kaggle/input/hospital-supply-chain/` for inventory, patient, staffing, and financial data. Obtain the source dataset and adjust the paths before running locally.

## Notes & Limitations

- Forecast quality depends on data quality, target definition, feature selection, and validation design.
- Treat model outputs as analytical estimates, not clinical recommendations.
- Review validation results in the notebook before using any prediction operationally.

## Next Improvements

- Add a reproducible train/validation split and baseline comparison.
- Report suitable regression metrics such as MAE and RMSE.
- Add a data dictionary and a concise summary of validated findings.

---
Created as a portfolio project to demonstrate a structured approach to healthcare operations and inventory analytics.