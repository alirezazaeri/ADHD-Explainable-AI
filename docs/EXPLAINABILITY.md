# Explainability

## Methods used

The experiment uses:

- fitted coefficients for Logistic Regression;
- built-in tree feature importance where requested;
- `shap.TreeExplainer` for Random Forest, XGBoost, and LightGBM;
- global SHAP bar and beeswarm summaries over the transformed held-out representation.

The selected README visuals explain the recorded XGBoost model globally. They do not provide a clinical explanation or establish why ADHD occurs in an individual.

## What the features mean

The models do not consume the raw source tables directly. Explanations operate on a 39-feature transformed representation containing selected psychometric variables, numeric demographic codes, 20 nonlinear Kernel PCA coordinates, and `Sex_F`.

Important interpretation constraints:

- SHAP values describe contributions within the fitted model, not causal effects;
- Kernel PCA components are latent coordinates, not directly interpretable brain regions, connections, biomarkers, or mechanisms;
- feature values in plots may be standardized rather than expressed in original units;
- low/high colour encodings are not inherently meaningful for nominal category codes;
- a low SHAP value for `Sex_F` does not prove the absence of proxy effects or establish fairness;
- the SHAP output scale depends on the explainer and model configuration and should not be assumed to be a probability change.

## Global versus local explanation

The retained SHAP plots are global summaries across held-out examples. No separately designed local explanation for a named participant is presented as a public project result.

Explanations from different fitted models are not interchangeable. Coefficient magnitude, tree split importance, and mean absolute SHAP value answer different questions and can change with scaling, correlation, background data, and model configuration. Their rankings should not be combined into a single universal feature hierarchy.

## Review checklist for public explanations

Before publishing or reusing an explanation, verify that it:

- names the fitted model and the evaluated partition;
- states whether the view is global or local;
- identifies that the input is the transformed 39-feature representation;
- distinguishes selected source variables from latent Kernel PCA coordinates;
- states whether plotted feature values are standardized or coded;
- avoids treating SHAP magnitude as causality, clinical importance, or effect size;
- carries forward the preprocessing-leakage and test-reuse limitations;
- contains no record-level values, identifiers, screenshots, or individual narratives;
- does not infer fairness from `Sex_F` importance alone.

An explanation that cannot satisfy these checks should remain unpublished or be relabeled as an exploratory technical artifact.

## Responsible interpretation

Use the explanation outputs to inspect model behaviour and generate technical questions. Do not use them to infer causation, identify clinical biomarkers, justify treatment, certify fairness, or explain an individual in a healthcare decision.
