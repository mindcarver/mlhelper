---
name: mlh
description: >-
  Use when starting, navigating, or governing a predictive machine-learning research study, especially before choosing data, features, models, test sets, or downstream validation.
metadata:
  category: discipline
  triggers: machine learning research, ML study, research pipeline, experiment workflow, model evaluation
---

# MLH research control

Treat predictive ML as evidence-preserving learning. Read [research-contract.md](references/research-contract.md) for all exposure, revision, validation-level, and authorization decisions; [artifact-contract.md](references/artifact-contract.md) for outputs; and [split-protocols.md](references/split-protocols.md) for dependent data.

## Route one request

| Intent | Skill |
|---|---|
| Provisional question, development-only feasibility, formal protocol, or revision | `mlh-frame` |
| Labels, availability, provenance, sealed audits, splits | `mlh-data` |
| Baselines, models, decision rules, inner validation, rolling procedure | `mlh-develop` |
| Locked predictive evaluation | `mlh-test` |
| Locked downstream value, including shared test predictions | `mlh-impact` |
| Untouched final holdout or prospective validation | `mlh-holdout` |
| Challenge evidence | `mlh-review` |
| Read-only state and earliest blocker | `mlh-status` |
| Immutable Git boundary | `mlh-freeze` |
| Evidence-supported conclusion or early stop | `mlh-conclude` |

For cross-stage planning start with status. Use `validation.level` to choose exploratory, confirmatory, or deployment requirements; do not force every pilot through seven stages.

## Non-negotiable rules

1. Bounded feasibility may use designated development data before formal framing. Record provisional assumptions, data exposure, and attempted variants. No independent claim from exploration.
2. Freeze the formal target, splits, primary metric, search budget, decision policy, and falsification rules before outer evaluation; frame/data are immutable before formal development.
3. Fit preprocessing, feature selection, resampling, calibration, threshold/policy selection, and tuning inside training folds.
4. Lock the whole learning and decision procedure. Scheduled rolling retraining is allowed only under frozen rules and point-in-time label availability.
5. Never redesign from outer results within a revision. New revisions inherit ancestor exposure; new names do not restore independence.
6. Audit sealed data without disclosing its outcomes. Known fixed time ranges are not equivalent to outcome access.
7. Test and impact may share samples/predictions, but are then two endpoints on one body of evidence.
8. Preserve all influential attempts, failures, and actual researcher decisions. Honor recorded authorization for routine progression without inventing approval or deploying.

Causal inference, reinforcement learning, and pure exploratory clustering require a separate method-specific protocol; predictive evidence alone cannot establish their claims.