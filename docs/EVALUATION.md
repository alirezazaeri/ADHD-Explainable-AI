# Evaluation

## Recorded results

The values below are preserved notebook outputs. They were not recomputed during publication preparation.

| Model | Mean CV F1 | Held-out accuracy | Held-out F1 | Held-out ROC AUC |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.8088 | 0.8049 | 0.8493 | 0.8853 |
| Random Forest | 0.8548 | 0.8104 | 0.8681 | 0.8610 |
| XGBoost | 0.8554 | 0.8269 | 0.8777 | 0.8619 |
| LightGBM | 0.8529 | 0.7912 | 0.8555 | 0.8482 |

XGBoost records the highest held-out accuracy and F1. Logistic Regression records the highest held-out ROC AUC. These rankings do not establish superiority outside this experiment.

The recorded XGBoost confusion matrix contains 75 true negatives, 40 false positives, 23 false negatives, and 226 true positives at the model's recorded decision threshold.

## Interpretation boundary

The held-out values are affected by full-cohort connectome preprocessing. The same held-out set is also reused for model comparison and final selection. Consequently, it functions partly as a selection set and is not an untouched final evaluation.

Accuracy summarizes total correct classifications. F1 summarizes the balance of precision and recall for the positive class. ROC AUC summarizes ranking across thresholds. None of these metrics alone determines clinical value, fairness, calibration, or an appropriate decision threshold.

## Evaluation not recorded

The historical workflow does not include:

- confidence intervals or cross-validation dispersion;
- precision and recall as headline results;
- PR AUC;
- calibration curves or Brier scores;
- threshold or decision-utility analysis;
- statistical comparison between models;
- external or prospective validation.

The figures under `docs/images/` visualize the same historical outputs and inherit the same limitations.
