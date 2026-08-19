---
name: mlh-data
description: >-
  Use when defining, building, or auditing ML labels, feature availability, dataset provenance, sample identity, train-test splits, temporal gaps, group leakage, or data adequacy.
metadata:
  category: discipline
  triggers: data leakage, label design, dataset split, temporal embargo, group split, data audit
---

# Establish trustworthy data

Data is complete only when another researcher can reconstruct who was eligible, what was knowable, and which split each sample belongs to.

## Preconditions

- The frame is substantive and frozen or otherwise immutably identified before label distributions or model-relevant evidence are inspected.
- Later-stage outcomes have not been inspected to choose data rules.
- The study route is predictive or has a separate approved protocol.

## Workflow

1. Trace each source from acquisition through joins and snapshot identity. Record versions, access constraints, revisions, and point-in-time semantics.
2. Define entity id, event time, prediction time, label start/end, target availability, and independent sampling unit.
3. Audit duplicates, correlated copies, entity overlap, future-derived fields, survivorship, selection bias, missingness, target proxies, and preprocessing fitted outside training folds.
4. Choose deterministic split membership or rules using `../mlh/references/split-protocols.md`. Add grouping, gap, embargo, purge, or spatial blocks when dependencies require them.
5. Quantify samples, target distribution, coverage, and uncertainty for every outer split without using outcome performance to move boundaries.
6. Produce the data-stage artifacts from `../mlh/references/artifact-contract.md` and append decisions to `RESEARCH.md`.

## Stop conditions

Stop when target timestamps are ambiguous, split identity is not reproducible, leakage cannot be excluded, or sample adequacy makes the planned estimate meaningless. Do not patch these issues after seeing test evidence; create a revision.

Never fit imputation, scaling, feature selection, resampling, calibration, or learned representations on all splits. Calling a transformation "unsupervised" does not exempt it.
