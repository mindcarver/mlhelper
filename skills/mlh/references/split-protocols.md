---
description: Guides selection of leakage-resistant inner validation, test, and holdout protocols for predictive ML studies.
metadata:
  tags: cross validation, time series, grouped split, spatial split, embargo
---

# Split protocols

Choose the split from the deployment dependency structure, not from convenience.

| Data relationship | Development protocol | Outer evidence |
|---|---|---|
| IID observations | Stratified or repeated K-fold when class balance matters | Independent test and holdout |
| Repeated entities | Grouped folds by entity or deployment unit | New groups, later observations, or both |
| Temporal prediction | Expanding or rolling folds; training always precedes validation | Later contiguous test and holdout windows |
| Overlapping temporal labels | Temporal folds plus gap/embargo at least large enough to remove label overlap | Later non-overlapping windows |
| Spatial dependence | Spatial blocks or leave-region-out | Unseen regions and, when relevant, later time |
| Hierarchical data | Group at the level expected to generalize | Unseen top-level groups |

## Protocol decisions to record

- unit of observation and independent sampling unit;
- entity, group, event time, label start, and label end;
- whether deployment predicts new rows, new entities, future periods, or new regions;
- inner-fold construction and number of folds;
- gap, embargo, purge, and maximum training window;
- stratification or weighting logic;
- immutable test and final-evidence membership or prospective accrual rules;
- validation level and whether extra final evidence is required by the original plan;
- test/impact shared samples and prediction artifacts, or distinct-data dependencies;
- development exploration membership, ancestor exposure, and real sealed access controls;
- random seed policy for stochastic splitters;
- sample adequacy and expected uncertainty.

## Rules

1. Designate development data before exploration. Within formal development, split before fitting imputation, scaling, feature selection, resampling, representation learning, calibration, or threshold/policy selection.
2. Keep all correlated copies, augmentations, sessions, and entities in the same side of a boundary unless deployment truly separates them.
3. Time-ordered problems never train on future observations to predict the past.
4. If the label interval overlaps a later fold, remove or embargo the contaminated observations.
5. Use nested evaluation when the reported cross-validation estimate is also affected by model or hyperparameter selection. Otherwise describe the inner validation score as selection evidence, not an unbiased generalization estimate.
6. Do not rebalance the outer test or holdout to make metrics look stable; report the deployment distribution and uncertainty.

## Outer rolling evaluation

An outer test or final window may evaluate a frozen sequential learning procedure. Predeclare fit cutoffs, training window, mature-label availability, permitted use of earlier evaluation observations, update/search budgets, calibration/policy changes, execution lag and failure fallback. Each prediction uses only information then available; never fit on its target or future labels. Earlier observations may become training data for later predictions only as specified before exposure.

This estimates a locked algorithm over time, not one unchanged fitted model. Preserve per-step data/model/prediction identities and use uncertainty appropriate for serial/group dependence. Human redesign based on outer results requires revision; automatic updates under frozen rules do not. Do not use sequential evaluation as a loophole for manual tuning.

Fixed time ranges and membership rules can be known before opening final evidence. Audit sealed labels only through the fixed disclosure policy in [research-contract.md](research-contract.md). Choosing a new revision or a new split name cannot erase exposure or overlapping-sample history.

## Red flags

- Random row split on users, patients, assets, stores, devices, or documents with repeated observations.
- Feature engineering performed once on the full dataset.
- Test labels available in a notebook used for error-driven feature design.
- A holdout window moved after its result was seen.
- Split choice justified only by a better score.
