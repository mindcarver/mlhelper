---
name: mlh-holdout
description: >-
  Use when test and impact are closed and a planned untouched holdout or prospective window is ready to evaluate a locked fixed or rolling ML system.
metadata:
  category: discipline
  triggers: final holdout, untouched data, final evaluation, model decay, external validation
---

# Open final evidence

Evaluate an untouched final holdout or a predeclared prospective window.

## Gate

Read [research-contract.md](../mlh/references/research-contract.md). Use this stage when `validation.final_evidence` is `holdout` or `prospective`; it is required for deployment advancement and optional only when the original confirmatory plan says so. Do not drop a planned final evaluation after bad results.

Before opening:
- Reconstruct inherited exposure and verify sealed outcomes. Known fixed time ranges or membership rules alone do not invalidate untouched status.
- Confirm test/impact reports and decisions are closed and immutable, with blocking findings resolved.
- Identify the exact complete learning/decision procedure, environment, evaluation code, metrics, decay comparisons, uncertainty, failures, and evaluation window.
- For prospective evidence, the plan must precede accrual of future outcomes; elapsed time alone is not proof of independence.
- Record the actual final-opening authorization; prior explicit authorization covering this checkpoint is sufficient.

## Workflow

1. Record first exposure, dataset and procedure identities, and mode in `exposure.yaml` and `holdout/holdout-report.md`.
2. Execute the locked system. Fixed models stay fixed; rolling systems follow frozen windows, updates, mature-label rules and fallbacks with per-step logs. No manual response to emerging outcomes.
3. Compare direction, magnitude, calibration, subgroup/time stability, decision impact and appropriate uncertainty against earlier expectations.
4. Report decay, anomalies, counter-evidence, and all failures without moving thresholds or excluding inconvenient observations.
5. Apply [artifact-contract.md](../mlh/references/artifact-contract.md); deployment advancement also needs the monitoring/exit plan and final review.

Exposed data cannot become untouched by a new revision, new name, or shifted convenient window. Material redesign inherits exposure and requires genuinely new evidence for independent claims. Preserve failed results; the same revision may diagnose, review, conclude, or make logged non-material reporting corrections.
