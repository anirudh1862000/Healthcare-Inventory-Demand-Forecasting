# Supply Chain in Healthcare

## Project Overview
This project analyzes hospital operations data across inventory, patient flow, staffing, and finance, then builds a model to predict inventory demand.

Notebook: `supply-chain-in-healthcare.ipynb`

## Datasets
The notebook loads four datasets:
- `/kaggle/input/hospital-supply-chain/inventory_data.csv`
- `/kaggle/input/hospital-supply-chain/patient_data.csv`
- `/kaggle/input/hospital-supply-chain/staff_data.csv`
- `/kaggle/input/hospital-supply-chain/financial_data.csv`

## Analysis Scope
- Data quality and structure summaries for each table
- Date normalization and combined dataframe creation
- Operational visualizations:
  - Stock vs min/max capacity
  - Staffing worked vs overtime
  - Expense category breakdown
  - Diagnosis vs procedures
  - Correlation heatmap (bed days, stock, capacity)
  - Inventory valuation and patient stay analysis
- Feature engineering for supply planning:
  - `Inventory_Shortfall`
  - `Replenishment_Needs`
- One-hot encoding for categorical variables
- Demand prediction with `GradientBoostingRegressor`

## Tech Stack
- Python
- Pandas
- Matplotlib
- Seaborn
- scikit-learn

## How to Run
1. Open `supply-chain-in-healthcare.ipynb`.
2. Install dependencies:
   - `pandas`
   - `matplotlib`
   - `seaborn`
   - `scikit-learn`
3. Update dataset paths if running outside Kaggle.
4. Execute all cells sequentially.

## Key Outcome
The notebook provides both operational insights and a predictive demand model that supports better inventory planning in hospital environments.
