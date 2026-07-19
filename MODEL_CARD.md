# Model card: ADHD Explainable AI

## Model overview

This repository preserves a retrospective machine-learning experiment comparing Logistic Regression, Random Forest, XGBoost, and LightGBM for binary classification of the recorded `ADHD_Outcome` label.

The selected historical model is XGBoost because it recorded the highest held-out accuracy and F1 in the four-model comparison. Logistic Regression recorded the highest ROC AUC.

## Intended use

The project is intended for education, portfolio demonstration, and retrospective research-method exploration. It demonstrates multimodal feature preparation, model comparison, global explanation, and exploratory subgroup reporting.

## Out-of-scope use

The models must not be used to:

- diagnose, screen, or rule out ADHD;
- replace a clinician or professional assessment;
- recommend treatment or services;
- make decisions about an individual;
- support clinical, regulatory, insurance, education, employment, or other high-stakes action;
- claim causal, biological, or diagnostic markers;
- certify fairness or legal compliance.

## Data and representation

The historical cohort contains 1,213 records from the WiDS Datathon 2025 data. The model representation contains 10 selected numeric/psychometric features, 8 selected demographic features, 20 connectome Kernel PCA components, and `Sex_F`.

The complete dataset is not redistributed. See [dataset setup](docs/DATASET_SETUP.md).

## Recorded performance

| Model | Accuracy | F1 | ROC AUC |
|---|---:|---:|---:|
| Logistic Regression | 0.8049 | 0.8493 | 0.8853 |
| Random Forest | 0.8104 | 0.8681 | 0.8610 |
| XGBoost | 0.8269 | 0.8777 | 0.8619 |
| LightGBM | 0.7912 | 0.8555 | 0.8482 |

These are preserved, leakage-affected held-out results. See [evaluation](docs/EVALUATION.md) and [methodology](docs/METHODOLOGY.md).

## Explainability

The project uses coefficients, feature importance, and global SHAP summaries. Explanations describe the fitted model in a transformed feature space; they do not establish causation or clinical meaning. See [explainability](docs/EXPLAINABILITY.md).

## Limitations

- connectome scaling and Kernel PCA use the full cohort before test-row selection;
- preprocessing and feature selection are outside CV folds;
- the held-out set is reused for model selection;
- categorical codes are modeled numerically;
- no calibration, uncertainty, external validation, or clinical validation is recorded;
- subgroup analysis is descriptive and incomplete;
- exact clean-environment reproducibility is not established.

## Ethical considerations

The source concerns children and adolescents and includes sensitive health, demographic, behavioural, and neuroimaging-derived data. Pseudonymisation does not remove all privacy or re-identification risk. Separate participant-level files must remain private and subject to provider terms.
