---
name: mlh-develop
description: >-
  Use when planning or performing baseline comparison, feature work, preprocessing, inner validation, hyperparameter search, ablation, experiment tracking, or recipe selection on training data.
metadata:
  category: discipline
  triggers: train model, tune hyperparameters, cross validation, feature engineering, baseline, experiment tracking
---

# Develop inside the training boundary

All choices that can improve the selected recipe belong here and nowhere later.

## Preconditions

- Frame and data artifacts are substantive, reviewed where required, and frozen or otherwise immutably identified.
- Inner folds reproduce the intended deployment boundary.
- Test, impact, and holdout labels or aggregate outcomes remain unexposed.

## Workflow

1. Run applicable naive, simple, and incumbent baselines before complex models.
2. Express preprocessing and learned feature steps as part of the fold-fitted recipe. Fit them separately inside each training fold.
3. Fix the allowed model families, search space, trial budget, seed policy, primary selection rule, tie-breakers, and stopping condition before searching.
4. Log every trial that influenced the search, including failed runs and manual variants. Record fold-level metrics, uncertainty, compute cost, rejection reason, and recipe identity.
5. Compare stability across folds, time, groups, classes, and seeds. Perform predeclared ablations and negative controls.
6. Select the least complex recipe adequately supported by evidence; do not select solely by the maximum mean score.
7. Complete `baselines.csv`, `experiments.csv`, `selection.md`, and `recipe.yaml`. Record budget use and remaining risks in `RESEARCH.md`.

## Iron boundary

Do not read test or holdout outcomes "to sanity-check" development. If any later evidence has already influenced a choice, preserve this revision and create a new one.

Development is not complete until recipe identity includes data/split versions, features, preprocessing, model, parameters, seeds, calibration or threshold logic, dependencies, and code revision.
