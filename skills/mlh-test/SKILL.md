---
name: mlh-test
description: >-
  Use when a fully locked ML recipe is ready for its first independent predictive evaluation, or when checking whether proposed test analysis would contaminate model selection.
metadata:
  category: discipline
  triggers: evaluate test set, out of sample test, locked model, test report, generalization estimate
---

# Run independent test evidence

Evaluate the locked procedure; do not use test to choose it.

## Gate

Read [research-contract.md](../mlh/references/research-contract.md). Exploratory studies do not open formal test evidence without an authorized formal plan.

Before exposure verify immutable frame/data/develop, substantive data/develop review, executable recipe identity, eligible test exposure history (including ancestors), and predeclared metrics/uncertainty, subgroup checks, failures, and decision policy. Verify actual researcher authorization; existing scope may cover this routine transition. Return to the earliest valid stage if prerequisites are missing.

## Workflow

1. Record data, split, code/environment, procedure, and first exposure identities in the report and `exposure.yaml`.
2. Fixed-model evaluation never refits on test. Rolling evaluation follows the frozen schedule using only information and matured labels available before each prediction. Earlier evaluation observations may enter subsequent training only under the explicitly predeclared rule; never use the row being scored or future labels.
3. Preserve fit cutoffs, label availability, fitted artifacts, predictions, decision times, and failed execution logs. Resume unchanged execution only without outcome-guided selection; do not rerun stochastic variants to choose a winner.
4. Report predeclared metrics, suitable uncertainty, baseline deltas, calibration, stability, concentration, and failures. Sequential observations are not IID-independent merely because each prediction is forward-looking.
5. Identify the immutable prediction artifact and whether impact reuses it. Such reuse is not another independent replication.
6. Write [test artifacts](../mlh/references/artifact-contract.md). Separate post hoc diagnostics from predeclared endpoints; record only actual researcher decisions or the applicable prior authorization.

After exposure, material redesign needs a linked revision and inherited exposure. Reusing its test after redesign is development/diagnosis, not a new independent estimate. Reporting corrections that leave predictions/samples unchanged may be logged in the same revision.