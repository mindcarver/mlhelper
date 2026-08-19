---
name: mlh-test
description: >-
  Use when a fully locked ML recipe is ready for its first independent predictive evaluation, or when checking whether proposed test analysis would contaminate model selection.
metadata:
  category: discipline
  triggers: evaluate test set, out of sample test, locked model, test report, generalization estimate
---

# Run independent test evidence

Test estimates predictive generalization; it does not choose a better recipe.

## Gate

Before opening test outcomes, verify:

- data and develop evidence are frozen or otherwise immutably identified;
- `recipe.yaml` is complete and matches the executable implementation;
- the test membership, primary metric, uncertainty method, subgroup checks, and failure criteria were predeclared;
- the prediction-to-decision policy for a later impact stage is already fixed when impact is claimed.

If any item is missing, stop before exposure and return to the earliest unexposed stage. If test evidence is already exposed, repair through a new revision.

## Workflow

1. Record recipe, data, code, environment, and split identities plus the exposure timestamp.
2. Apply the locked recipe without refitting on test data. Compute only predictions and predeclared diagnostics.
3. Report primary and secondary metrics, uncertainty, baseline deltas, calibration where relevant, subgroup/time stability, concentration, and failures.
4. Separate observations from explanations. Do not recommend a same-revision feature, threshold, exclusion, ensemble, or hyperparameter change.
5. Write `test/test-report.md` and append the researcher's decision to `RESEARCH.md` only when the researcher provides it.

An execution failure may be retried only when no outcome was exposed and the retry does not change the recipe. Preserve logs explaining the retry.
