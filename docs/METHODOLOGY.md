# Historical methodology

## Scope

This document describes the experiment recorded in the published notebooks. It does not redefine, rerun, or correct the historical workflow.

The task is binary classification of the recorded `ADHD_Outcome` label from psychometric, demographic, and functional-connectome features. `Sex_F` is retained as a model input and is also used for exploratory subgroup evaluation.

## Recorded data preparation

1. Merge four local inputs by `participant_id`.
2. Form a combined sex/outcome stratification label.
3. Split 1,213 records into 849 training and 364 held-out records using a stratified 70/30 split and `random_state=42`.
4. Fit a five-neighbour KNN imputer on numeric training metadata and transform the test metadata.
5. Fill missing coded demographic values with `3`, described in the notebook as unknown.
6. Use mutual information on the training partition to retain 10 numeric/psychometric and 8 demographic features.
7. Standardize the 19,900 connectome measurements and transform them into 20 RBF Kernel PCA components using `gamma=0.001`.
8. Combine selected metadata, connectome components, `Sex_F`, and the target.
9. Standardize model inputs using training-set statistics while leaving `Sex_F` unscaled.

The final model representation contains 39 inputs: 10 numeric/psychometric features, 8 demographic features, 20 Kernel PCA components, and `Sex_F`.

## Recorded model selection

Four classifiers are compared:

- Logistic Regression;
- Random Forest;
- XGBoost;
- LightGBM.

Hyperparameters are selected with five-fold shuffled `StratifiedKFold` cross-validation using F1 as the score and `random_state=42`. Logistic Regression uses grid search; the ensemble models use randomized search with 10 sampled configurations.

The notebooks report accuracy, F1, ROC AUC, confusion matrices, model-level explanation outputs, and exploratory sex-disaggregated metrics.

## Known methodological limitations

The experiment is preserved with the following limitations:

- the connectome scaler and Kernel PCA are fit to all 1,213 rows before train/test rows are selected, exposing the transformation to held-out feature distributions;
- imputation, feature selection, connectome transformation, and model scaling are established outside the cross-validation folds;
- the same held-out set is used to compare four models and select the final model, so it is not an untouched post-selection test set;
- several nominal demographic variables are represented by numeric codes and modeled numerically;
- class-balancing strategies differ across models, and the selected LightGBM configuration assigns a positive-class weight of 2 even though the positive label is the majority class;
- there is no external, temporal, or site-held-out validation;
- no uncertainty intervals, calibration analysis, PR AUC, or decision-utility analysis are recorded.

These limitations mean that the recorded scores should be treated as historical, internally evaluated results rather than unbiased estimates of future, clinical, or production performance.
