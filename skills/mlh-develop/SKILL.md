---
name: mlh-develop
description: >-
  Use when planning or performing baseline comparison, feature work, preprocessing, inner validation, hyperparameter search, ablation, experiment tracking, or recipe selection on training data.
metadata:
  category: discipline
  triggers: train model, tune hyperparameters, cross validation, feature engineering, baseline, experiment tracking
---

# Develop inside the training boundary

Select the learning procedure and its decision rules using development evidence only.

## Gate

Read [research-contract.md](../mlh/references/research-contract.md) and [artifact-contract.md](../mlh/references/artifact-contract.md). Formal development requires substantive immutable frame/data. A requested bounded exploratory pilot needs a provisional frame, development identity, and budget; label its result exploratory.

Outer evidence designated for a fresh independent claim must not have influenced this or any ancestor's selection. Inherited exposed data may be explicitly reassigned to development/diagnosis, never restored as independent evidence.

## Workflow

1. Run applicable naive, simple, incumbent, and decision-policy baselines before complexity.
2. Put preprocessing, feature learning/selection, resampling, calibration, and threshold/policy tuning inside training folds.
3. Fix search families/space, trial budget, seeds, selection metric, tie-breakers, and stopping rules. Include manual policy variants, pilot attempts, and cumulative ancestor attempts in the log. An approved new budget does not erase selection history.
4. Jointly compare prediction and intended decision value inside inner validation using declared costs and constraints. If net decision value is the primary claim, use the predeclared selection rule; do not postpone all policy design until impact.
5. Assess fold/time/group/seed stability, uncertainty, predeclared ablations and negative controls. Do not treat the best inner score as an unbiased performance estimate.
6. Select the least complex adequately supported procedure. Complete baselines, experiments, selection, and recipe artifacts, or mapped pilot records.
7. Lock fixed-model identity or the full rolling algorithm: training window, schedule, mature-label rule, allowed prior evaluation data, feature/parameter selection and update budget, calibration/policy updates, seeds, lag, and failure fallback. Fix these rules before outer exposure; preserve per-step provenance during execution.
8. Complete the pre-outer data/develop review and record remaining risks before formal test.

Reading later outcomes to choose features, thresholds, sample exclusions, cost rules, or retraining frequency requires revision and inherited exposure. Scheduled retraining under the locked algorithm is allowed; manual post-result redesign is not.