---
description: Defines MLH stage order, evidence boundaries, revision rules, and prohibited research shortcuts.
metadata:
  tags: research governance, stage gates, leakage, revisions
---

# Research contract

## Stage order

```text
frame -> data -> develop -> test -> impact -> holdout -> conclude
```

`review` may challenge any stage. `status` is always read-only. `freeze` records a stage boundary but does not make weak evidence valid.

## Two loops

The inner loop belongs entirely inside `develop`:

```text
baseline -> features -> preprocessing -> model -> inner validation -> ablation -> selection
```

The outer loop estimates how well the locked recipe survives new evidence. Test, impact, and holdout are not extra tuning sets.

## Evidence exposure

A stage is exposed when its labels, aggregate metrics, charts, predictions, or qualitative outcome have been inspected by anyone choosing the recipe. Hiding filenames or withholding one metric does not make exposed evidence untouched again.

After test exposure, the same revision may:

- diagnose the locked recipe;
- correct a reporting error without changing predictions;
- document limitations and alternative explanations;
- continue to a predeclared impact protocol.

It may not change features, preprocessing, model family, hyperparameters, thresholds, ensemble weights, sample exclusions, primary metric, or decision policy. Those changes require a new revision with `revision.parent_id` and `revision.reason`.

## Material changes

Treat a change as material when it can change predictions, evaluated samples, selection, or the claimed conclusion. Examples include a bug fix in label construction, a new missing-value rule, a different random seed policy, or a revised cost model.

Pure prose corrections and additional diagnostics computed from already exposed outputs are not material when they do not influence a new recipe claim. Record both kinds of change.

## Split roles

- **Train:** model fitting and all inner validation.
- **Test:** one independent estimate of predictive generalization for the locked recipe.
- **Impact:** predeclared mapping from predictions to decisions and downstream consequences.
- **Holdout:** final untouched evidence, opened only after test and impact decisions are closed.

Impact may be marked `not_applicable` only when the study makes no downstream decision or intervention claim. Predictive metrics must not be relabeled as impact.

## Stop conditions

Stop or create a revision when:

- leakage or target ambiguity invalidates earlier evidence;
- the search budget is exhausted;
- a kill criterion is met;
- test evidence has been viewed and a recipe change is proposed;
- holdout has been viewed and further model development is proposed.

Preserve failed studies. A negative result is evidence, not clutter.

## Common rationalizations

| Excuse | Reality |
|---|---|
| "I only peeked at test once" | One peek can influence selection; the evidence is exposed. |
| "The preprocessing is unsupervised" | It can still leak distribution information and bias evaluation. |
| "This fix is obviously harmless" | If predictions or evaluated samples can change, it is material. |
| "We need one more hyperparameter" | A search budget is meaningful only when it stops the search. |
| "Holdout is just another test" | Reusing it converts it into development evidence. |
| "The model metric is strong, so impact is obvious" | Prediction quality and decision value are different claims. |
