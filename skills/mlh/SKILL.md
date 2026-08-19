---
name: mlh
description: >-
  Use when starting, navigating, or governing a predictive machine-learning research study, especially before choosing data, features, models, test sets, or downstream validation.
metadata:
  category: discipline
  triggers: machine learning research, ML study, research pipeline, experiment workflow, model evaluation
---

# MLH research control

Treat ML research as an evidence-preserving process, not a search for the highest score.

## Route one request

| Intent | Skill |
|---|---|
| Define or revise a study before evidence is exposed | `mlh-frame` |
| Audit labels, availability, provenance, or splits | `mlh-data` |
| Build baselines, inner validation, experiments, or select a recipe | `mlh-develop` |
| Evaluate the locked recipe on independent test data | `mlh-test` |
| Convert predictions into decisions, simulations, or economic results | `mlh-impact` |
| Run the untouched final evaluation | `mlh-holdout` |
| Challenge evidence or assumptions | `mlh-review` |
| Inspect current state without writing | `mlh-status` |
| Create an auditable Git boundary | `mlh-freeze` |
| Decide what the evidence supports | `mlh-conclude` |

For cross-stage planning, use `mlh-status` first. Read [research-contract.md](references/research-contract.md) when deciding whether an action is allowed, [artifact-contract.md](references/artifact-contract.md) when checking outputs, and [split-protocols.md](references/split-protocols.md) when choosing evaluation splits.

## Non-negotiable rules

1. Define the target, decision context, split protocol, primary metric, search budget, and falsification criteria before development.
2. Complete and freeze, or otherwise immutably identify, each stage before exposing evidence from the next one.
3. Fit preprocessing, feature selection, resampling, calibration, and model tuning only inside training folds.
4. Never use test, impact, or holdout evidence to select a recipe for the same study revision.
5. Exposing later-stage evidence closes earlier design choices. Any material change requires a new revision linked to the old one.
6. Record every attempted variant that influenced selection, including failures.
7. Separate predictive quality from downstream impact.
8. Report evidence and uncertainty; the researcher records the decision.

If the request is causal inference, reinforcement learning, or pure exploratory clustering, state that this predictive protocol is insufficient and establish a method-specific protocol before proceeding.
