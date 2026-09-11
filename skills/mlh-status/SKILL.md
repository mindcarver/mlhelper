---
name: mlh-status
description: >-
  Use when checking the current stage, evidence completeness, freeze state, exposure history, unresolved review findings, or the single next action for an MLH study.
metadata:
  category: reference
  triggers: MLH status, research progress, next step, stage complete, frozen evidence
---

# Inspect study status

This skill is read-only: do not create, repair, freeze, or migrate records.

1. Locate and read `study.yaml`, `RESEARCH.md`, `exposure.yaml`, stage evidence, and reviews. Apply [research-contract.md](../mlh/references/research-contract.md) and [artifact-contract.md](../mlh/references/artifact-contract.md).
2. Determine validation level and original required route. Exploratory pilots can conclude from development evidence; confirmatory may omit extra final evidence only when planned; deployment advancement requires final/prospective evidence and monitoring. An early stop does not mean all planned stages completed.
3. For schema version 1 or missing fields, preserve the original requirements, report absent level/exposure/procedure information, and do not infer a lighter level or untouched state. Mapping needs an authorized evidence-backed update.
4. Reject placeholders and empty tables. Verify immutable data, procedure, predictions and Git tags/manifest identities, including rolling step provenance where relevant.
5. Reconstruct ancestor and overlapping-data exposure, actual access controls, and disclosures. Missing history means independence is unverified. Test/impact reuse must be reported as shared evidence.
6. Check substantive review checkpoints, unresolved findings, actual researcher decisions, and prior authorization scope. A routine authorized transition is not blocked merely because it lacks a duplicate human signature.
7. Identify the earliest unmet requirement for the requested next action. Do not open sealed data to complete this inspection.

Report each stage as `not started`, `artifacts present`, `review open`, `frozen`, `invalidated`, `complete`, or `not required` (with plan-based reason). Separately state achieved evidence and original-plan completeness. End with one smallest valid next action. Do not equate a metric threshold, file existence, or a YAML access flag with validity.