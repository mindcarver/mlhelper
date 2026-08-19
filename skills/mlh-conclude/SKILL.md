---
name: mlh-conclude
description: >-
  Use when synthesizing completed ML evidence into supported claims, limitations, boundary conditions, a stop-or-revise decision, or a recommendation to monitor or advance.
metadata:
  category: technique
  triggers: conclude ML study, research verdict, evidence synthesis, model recommendation, negative result
---

# Conclude from the evidence

A conclusion states what the evidence supports, not what the researcher hoped to prove.

## Workflow

1. Verify stage and exposure status with `mlh-status`. State whether the conclusion is development-only, test-supported, impact-supported, or holdout-supported.
2. Reconstruct the original question, hypothesis, counter-hypothesis, success/failure criteria, and kill criteria without rewriting them to fit results.
3. Build a claim-evidence map covering predictive performance, uncertainty, baseline increment, stability, downstream impact, counter-evidence, and review findings.
4. Distinguish direct observations, statistical inferences, mechanism speculation, and operational assumptions.
5. State generalization boundaries by population, time, region, regime, label definition, decision policy, and data availability.
6. Record one researcher-approved decision:
   - `stop`: evidence is negative, invalid, or not worth continuing;
   - `revise`: a new hypothesis or material design change deserves a linked revision;
   - `monitor`: evidence is promising but prospective evidence is needed;
   - `advance`: evidence supports the explicitly named next validation or deployment step.
7. Update the Conclusion section of `RESEARCH.md` only when asked to record the decision.

If holdout is absent, do not call the conclusion final. If causal evidence is absent, do not claim mechanism or intervention causality. Preserve negative and inconclusive studies.
