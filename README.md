# Healthcare Inventory & Demand Planning Analysis

A portfolio project exploring hospital inventory, patient, staffing, and financial data with Python. The current notebook demonstrates exploratory analysis and a prototype demand-planning calculation.

> **Current status:** EDA and a prototype Gradient Boosting workflow are present. The model is **not yet validated as a genuine forecasting model**. Review the modeling caveats below before using it in a resume or interview.

## Business Questions

- How does stock compare with minimum requirements and maximum capacity?
- Which items may need replenishment when usage and supplier lead time are considered?
- What patterns appear in staffing, patient activity, and financial records?
- What additional data would be needed for a reliable item-level demand forecast?

## Data

The notebook expects four CSV files from the Kaggle dataset directory:

- `inventory_data.csv`
- `patient_data.csv`
- `staff_data.csv`
- `financial_data.csv`

The original notebook uses Kaggle paths under `/kaggle/input/hospital-supply-chain/`. Download the source data from the original dataset page and update the paths for your environment. Do not commit raw data unless its license and redistribution terms have been checked.

## Existing Workflow

1. Load and profile the four operational datasets.
2. Parse date columns and explore inventory, patient, staffing, and financial patterns.
3. Calculate stock value, estimated demand, inventory shortfall, and replenishment need.
4. Encode categorical columns and train a prototype `GradientBoostingRegressor`.
5. Review validation and test mean absolute error and a predicted-versus-actual plot.

## Important Modeling Caveats

The current notebook is a prototype, not a defensible production forecast:

- It combines the four datasets side-by-side with `pd.concat(..., axis=1)`. This assumes row 1 in each file describes the same observation; the notebook does not establish a shared key or validate that assumption.
- It fills missing values with zero across the combined data. Zero may be a valid quantity for some fields but is not a safe general replacement for missing patient, staffing, or financial values.
- The target is defined as `Estimated_Demand = Avg_Usage_Per_Day * Restock_Lead_Time`. This is a formula-derived replenishment estimate, not observed future demand.
- The model feature set retains `Avg_Usage_Per_Day` and `Restock_Lead_Time`, the two inputs used to calculate the target. This creates direct target leakage and makes the reported MAE unsuitable as evidence of future forecasting performance.
- The notebook uses a random train/validation/test split rather than a time-based split. That does not test whether the model can predict later periods from earlier observations.

**Do not quote the notebook's MAE as real-world forecast accuracy.** A valid forecasting redesign needs a clearly defined future-demand target, correctly joined records at a documented grain, features available at prediction time, and chronological holdout evaluation against a simple baseline.

## Recommended Next Version

1. Confirm the dataset source, field definitions, row grain, and join keys.
2. Build an item-by-date demand table from actual usage/consumption records, if the source contains them.
3. Define a future horizon (for example, next 7 or 30 days) and construct the target from future observed usage.
4. Exclude target-derived and future information from model features.
5. Use chronological train/validation/test windows and compare with a naive or moving-average baseline.
6. Report MAE and RMSE by item and forecast horizon; inspect residuals and error by demand level.
7. Keep inventory policy calculations (safety stock, reorder point, lead-time demand) separate from the statistical forecast.

## Tools

- Python, Pandas, NumPy
- Matplotlib, Seaborn
- scikit-learn, Gradient Boosting
- Data profiling, EDA, feature engineering, regression evaluation

## Run

1. Clone the repository and install `pandas`, `numpy`, `matplotlib`, `seaborn`, and `scikit-learn`.
2. Download the source CSV files and place them in a local data directory.
3. Update the four input paths at the top of `supply-chain-in-healthcare.ipynb`.
4. Run the notebook from top to bottom.
5. Treat the existing model metrics as prototype-only until the leakage and data-alignment issues above are resolved.

## Portfolio Presentation

This project currently demonstrates healthcare operations EDA and a prototype inventory-demand calculation. Present the machine-learning section as work in progress, not as a validated demand-forecasting result.
