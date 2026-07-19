# Fairness and bias

## Recorded subgroup analysis

The modeling notebook calculates accuracy, F1, and ROC AUC separately for the two recorded `Sex_F` groups. For XGBoost, the preserved results are:

| Recorded group | Accuracy | F1 | ROC AUC |
|---|---:|---:|---:|
| `Sex_F = 1` | 0.8240 | 0.8590 | 0.8712 |
| `Sex_F = 0` | 0.8285 | 0.8858 | 0.8492 |

These are descriptive subgroup results from one held-out split. They are not a fairness certification.

## What the analysis does not establish

The historical workflow does not include:

- confidence intervals or significance tests for subgroup differences;
- subgroup calibration or threshold analysis;
- false-positive-rate, false-negative-rate, equalized-odds, or predictive-parity assessment;
- intersectional analysis;
- external subgroup validation;
- an analysis of proxy variables or counterfactual fairness;
- a documented fairness objective or acceptance threshold.

`Sex_F` is both a model feature and the grouping attribute. Similar aggregate scores do not prove that model behaviour is fair, unbiased, or appropriate for individuals. Low SHAP importance for `Sex_F` also does not remove the need to examine proxy features, interactions, and errors.

## Responsible wording

Describe the results as **exploratory sex-disaggregated performance**. Do not describe the model as bias-free, gender-neutral, universally fair, or validated for healthcare use.
