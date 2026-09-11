---
name: mlh-review
description: >-
  Use when ML research evidence, experiment selection, leakage risk, generalization, robustness, downstream impact, or a stage transition needs an independent adversarial review.
metadata:
  category: technique
  triggers: adversarial review, research audit, leakage review, robustness check, challenge ML results
---

# Adversarial research review

Try to invalidate the claim using existing evidence before asking for more experiments.

1. Identify stage, validation level, original plan, claimed conclusion, immutable identities, and selector access history.
2. Read [research-contract.md](../mlh/references/research-contract.md) and [artifact-contract.md](../mlh/references/artifact-contract.md). Review requirements depend on level; one substantive review may cover multiple stages if each identity and finding is explicit.
3. Separate blocking integrity failures from uncertainty, practical limits, and optional improvements.
4. Challenge the applicable categories:
   - target/availability ambiguity, entity or temporal overlap, preprocessing and target-proxy leakage;
   - ancestor exposure, renamed/overlapping datasets, missing access history, and sealed-audit disclosure;
   - weak baselines, cumulative search multiplicity, manual variants, seeds, and selective reporting;
   - prediction and policy selection outside inner validation;
   - rolling cutoffs, mature labels, update budgets, fallbacks, and drift from frozen rules;
   - shared test/impact evidence incorrectly counted as independent replication;
   - calibration, subgroup failure, shift, concentration, uncertainty, negative controls;
   - costs, capacity, harms, feedback, simulation realism, final evidence and monitoring when required.
5. For each finding cite evidence or its absence, explain its effect on the claim, and name the earliest valid repair. A revision does not restore exposed data.
6. Check researcher decisions and authorization against actual records, not generated placeholders.

Use `blocking`, `warning`, or `info`. Link reviewed commit/manifest identities and unresolved findings. Do not enter a researcher's decision or turn review into same-revision tuning. A bounded exploratory conclusion need not pass deployment gates; a deployment claim may not silently downgrade its planned requirements.