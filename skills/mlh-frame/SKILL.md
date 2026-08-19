---
name: mlh-frame
description: >-
  Use when a predictive ML idea needs a study question, target, decision context, falsification criteria, metrics, search budget, or a new revision before data or model development.
metadata:
  category: technique
  triggers: frame ML study, research question, prediction target, success criteria, new ML experiment
---

# Frame an ML study

Create a falsifiable research protocol before evidence can influence design.

## Workflow

1. Locate the intended project root and check for an existing `studies/<id>`. Discussion-only requests do not authorize file creation.
2. State the claim class. MLH directly supports predictive classification, regression, ranking, and forecasting. Do not turn predictive association into a causal claim.
3. Define the real decision, unit of observation, prediction timestamp, target interval, horizon, availability lag, population, and exclusions.
4. Write one hypothesis and the strongest counter-hypothesis. Add observable kill criteria.
5. Select a split family appropriate to deployment. Read `../mlh/references/split-protocols.md` when the dependency structure is not trivial.
6. Predeclare the primary metric, uncertainty method, guardrails, baselines, allowed model families, maximum trials, selection rule, and downstream impact protocol.
7. Define success and failure without consulting test or holdout evidence.
8. For a new study, instantiate `study.yaml` and `RESEARCH.md` from `../mlh/assets/`. For a post-exposure redesign, create a new id and populate `revision.parent_id` and `revision.reason`.

## Quality checks

- The question names what is predicted, for whom, when, and for what decision.
- Target data is actually observable after the prediction timestamp.
- Metrics reflect the claim and deployment costs, not convenience.
- `max_trials: 0` is not accepted for an active search.
- Empty placeholders do not count as framing.

End with unresolved assumptions and the smallest next action. Do not start data analysis unless the user requested it.
