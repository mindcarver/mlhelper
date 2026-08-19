---
name: mlh-review
description: >-
  Use when ML research evidence, experiment selection, leakage risk, generalization, robustness, downstream impact, or a stage transition needs an independent adversarial review.
metadata:
  category: technique
  triggers: adversarial review, research audit, leakage review, robustness check, challenge ML results
---

# Adversarial research review

Try to invalidate the claim with the existing evidence before proposing more experiments.

## Review procedure

1. Identify the exact stage, claimed conclusion, frozen identities, and evidence that was available when choices were made.
2. Read the relevant completion contract in `../mlh/references/artifact-contract.md` and the exposure rules in `../mlh/references/research-contract.md`.
3. Separate blocking integrity failures from statistical uncertainty, practical limitations, and optional improvements.
4. Challenge at least the applicable categories:
   - target ambiguity and timestamp leakage;
   - split mismatch, group overlap, label overlap, and preprocessing leakage;
   - baseline weakness, search multiplicity, seed sensitivity, and selective reporting;
   - recipe identity drift between develop and later stages;
   - calibration, subgroup failure, distribution shift, concentration, and uncertainty;
   - simpler explanations, negative controls, and mechanism proxies;
   - decision costs, capacity, harms, feedback, and unrealistic simulation assumptions.
5. For each finding, cite the artifact or missing evidence, explain impact on the claim, and propose the earliest valid repair stage.

## Output

Use severity `blocking`, `warning`, or `info`. End with open questions and the exact decisions required from the researcher. Do not fill `Researcher Decision` on the researcher's behalf and do not turn a review into a same-revision tuning session.
