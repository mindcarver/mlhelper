---
name: mlh-holdout
description: >-
  Use when test interpretation and downstream policy are closed and an untouched final dataset is ready for one-shot evaluation of the complete locked ML system.
metadata:
  category: discipline
  triggers: final holdout, untouched data, final evaluation, model decay, external validation
---

# Open the final holdout

Holdout is the last untouched evidence, not a reserve tuning set.

## Gate

Confirm before exposure:

- holdout membership and labels were inaccessible to recipe selection and impact design;
- test and impact reports contain closed researcher decisions and are frozen or otherwise immutably identified;
- recipe, decision policy, code, dependencies, and evaluation code are immutably identified;
- expected metrics, decay comparisons, uncertainty, and failure rules are predeclared.

If the holdout has already influenced any choice, it is not a holdout. State the limitation and do not restore the label by renaming another convenient split.

## Workflow

1. Record the exposure timestamp and all identities.
2. Run the complete locked system once.
3. Compare direction, magnitude, calibration, subgroup stability, impact, and uncertainty against train/test expectations.
4. Quantify decay without moving thresholds or excluding inconvenient samples.
5. Write `holdout/holdout-report.md` and document anomalies, counter-evidence, and boundary conditions.

After exposure, any material redesign requires a new revision. The same revision may only diagnose, review, conclude, or correct non-predictive reporting errors.
