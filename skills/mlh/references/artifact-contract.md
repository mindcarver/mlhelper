---
description: Lists the minimum evidence artifacts and completion conditions for each MLH research stage.
metadata:
  tags: artifacts, completion criteria, study workspace, evidence
---

# Artifact contract

The recommended study root is `studies/<study-id>/`. Equivalent names are acceptable when the mapping is explicit in `study.yaml`.

## Workspace

```text
studies/<study-id>/
|-- study.yaml
|-- RESEARCH.md
|-- data/
|   |-- data-card.md
|   |-- split-manifest.yaml
|   `-- leakage-audit.md
|-- develop/
|   |-- baselines.csv
|   |-- experiments.csv
|   |-- selection.md
|   `-- recipe.yaml
|-- test/
|   `-- test-report.md
|-- impact/
|   `-- impact-report.md
|-- holdout/
|   `-- holdout-report.md
`-- reviews/
```

Large datasets, predictions, and serialized models may live outside Git. Record immutable URIs, versions, hashes, and generation code instead of committing them blindly.

## Completion by stage

### frame

- `study.yaml` contains a substantive question, prediction target, decision context, hypothesis, counter-hypothesis, scope, kill criteria, split roles, metrics, and search budget.
- `RESEARCH.md` records the framing decision and unresolved assumptions.
- No test or holdout evidence was used to set the protocol.

### data

- `data-card.md` records source, license/access constraints, unit of observation, entity/time keys, population, exclusions, missingness, and known bias.
- `split-manifest.yaml` identifies immutable split membership or deterministic rules plus label horizon, gap/embargo, grouping, and seed where relevant.
- `leakage-audit.md` checks feature availability, label overlap, duplicates, entity overlap, revisions, preprocessing, and target proxies.
- Data snapshot identity is reproducible.

### develop

- `baselines.csv` includes naive, simple, and incumbent baselines that apply.
- `experiments.csv` contains every trial that influenced selection, with recipe identity, fold metrics, uncertainty, status, and rejection reason.
- `selection.md` explains tradeoffs, ablations, stability, budget usage, and why the selected recipe is justified.
- `recipe.yaml` fully identifies data/split versions, features, preprocessing, model, hyperparameters, seeds, calibration, threshold or ranking rule, dependencies, and code revision.

### test

- The evaluated recipe identity matches frozen develop evidence.
- `test-report.md` reports the predeclared metrics, uncertainty, baseline deltas, subgroup/time stability, failures, and exposure timestamp.
- No alternative recipe was selected using test results.

### impact

- The prediction-to-decision policy and constraints were declared before running the evaluation.
- `impact-report.md` separates gross prediction quality from costs, capacity, latency, harms, risk, and sensitivity assumptions.
- If not applicable, the report states why and limits the claim accordingly.

### holdout

- The holdout remained inaccessible during development, test interpretation, and impact design.
- `holdout-report.md` identifies the exact locked recipe and reports decay, direction, stability, uncertainty, and failures without redesign.

### conclude

- `RESEARCH.md` links each claim to evidence, distinguishes observation from inference, lists limitations and counter-evidence, and records one decision: stop, revise, monitor, or advance.
- Any revision has a new id and preserves the parent evidence.
