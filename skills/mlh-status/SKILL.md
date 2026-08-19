---
name: mlh-status
description: >-
  Use when checking the current stage, evidence completeness, freeze state, exposure history, unresolved review findings, or the single next action for an MLH study.
metadata:
  category: reference
  triggers: MLH status, research progress, next step, stage complete, frozen evidence
---

# Inspect study status

This skill is read-only. Do not create, update, freeze, or repair artifacts while reporting status.

## Workflow

1. Locate the study root and parse `study.yaml`; report framing errors separately.
2. Read `RESEARCH.md` and stage artifacts. File existence alone is not evidence: reject placeholders, empty tables, missing identities, and reports without substantive results.
3. Apply `../mlh/references/artifact-contract.md` in stage order: frame, data, develop, test, impact, holdout, conclude.
4. Inspect Git history and annotated `mlh-<stage>-<study-id>` tags when the project uses Git. Confirm the tag points to a commit containing the reported artifacts.
5. Check reviews for substantive findings and an explicit researcher decision. A generated prompt or empty decision is still open.
6. Reconstruct exposure history. Flag later-stage outcomes that appear before their prerequisites were locked.
7. Treat the earliest incomplete or invalid stage as the current blocker.

## Report

For each stage use: `not started`, `artifacts present`, `review open`, `frozen`, `invalidated`, or `complete`. Then state one smallest next action. Never report PASS/FAIL merely because a metric crossed a threshold; compare evidence with the predeclared criteria and leave the decision to the researcher.
