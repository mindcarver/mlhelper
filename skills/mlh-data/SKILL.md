---
name: mlh-data
description: >-
  Use when defining, building, or auditing ML labels, feature availability, dataset provenance, sample identity, train-test splits, temporal gaps, group leakage, or data adequacy.
metadata:
  category: discipline
  triggers: data leakage, label design, dataset split, temporal embargo, group split, data audit
---

# Establish trustworthy data

Reconstruct what was knowable at prediction time, who was eligible, and the real access history.

## Gate and workflow

1. Read [research-contract.md](../mlh/references/research-contract.md). A provisional frame plus designated development data is sufficient for requested feasibility exploration. Formal data audit uses the substantive frame; frame/data are locked before formal model selection.
2. Trace source, versions, license/access, joins, revisions, and snapshot identity. Define entity, event/prediction time, label start/end, availability lag, and independent sampling unit.
3. Reconstruct `exposure.yaml`, including inherited history and overlapping/re-exported data. Separate actual access controls from declared roles. Unknown access blocks independent claims.
4. Audit development labels, duplicates, missingness, selection/survivorship bias, future fields, target proxies, overlap, and preprocessing leakage.
5. For test/final evidence release only predeclared structural information. Fixed membership rules/time ranges and hashes may be known; labels, target distributions, predictions, and outcomes remain sealed. Use development estimates for adequacy, or fixed isolated checks with approved coarse pass/block disclosure. Log each disclosure; do not probe outcome distributions with adaptive checks.
6. If isolation is unavailable, defer sealed outcome checks until authorized evaluation. Do not inspect them simply to finish an audit checklist. If outcomes were disclosed, record exposure; renaming data or creating a revision does not undo it.
7. Choose reproducible splits using [split-protocols.md](../mlh/references/split-protocols.md). Declare test/impact shared membership/predictions, dependencies, label availability, grouping, gap/purge, and the full rolling schedule where applicable.
8. Produce [data artifacts](../mlh/references/artifact-contract.md), record deferred sealed checks and decisions, and immutably identify formal data rules.

Stop for ambiguous target timestamps, unreproducible membership, unresolved leakage, or evidence too weak for the planned claim. Pilot uncertainty may be documented for feasibility; it is not a license for a confirmatory claim. Fit learned transformations only on eligible training folds.