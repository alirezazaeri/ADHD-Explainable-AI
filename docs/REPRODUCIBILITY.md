# Reproducibility

## Preserved environment information

Notebook metadata records Python 3.12.7 and a Python 3 ipykernel. Direct dependencies are listed in `requirements.txt`, but their versions were not recorded. The two notebooks retain the original execution counts, figures, tables, and metrics and were not rerun during publication preparation.

## Local workflow

Run from the `notebooks/` directory in this order:

1. `01_data_exploration.ipynb`
2. `02_modeling_and_testing.ipynb`

The first notebook reads authorized inputs from `../data/` and creates ignored derived CSV files under `final_datasets/`. The second notebook reads those local derived files.

## Randomness controls

The recorded workflow uses `random_state=42` for the train/test split, mutual information, Kernel PCA, cross-validation, and model searches. Seeds improve repeatability but do not guarantee identical output across package versions, platforms, or parallel implementations.

## Current reproducibility status

Exact end-to-end reproduction has not been established in a clean environment. Important reasons include:

- unpinned package versions;
- changing SHAP, XGBoost, LightGBM, and scikit-learn interfaces;
- notebook execution-order dependencies;
- local provider-controlled data access;
- learned preprocessing outside cross-validation folds;
- no automated test suite or environment lock.

The preserved historical outputs and a future corrected experiment are different reproducibility targets. Moving learned preprocessing inside training and validation boundaries would change the method and may change the results; such work should be versioned as a new experiment rather than silently replacing the historical record.
