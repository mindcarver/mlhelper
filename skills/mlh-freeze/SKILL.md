---
name: mlh-freeze
description: >-
  Use when a requested or previously authorized MLH stage freeze needs an exact Git commit and annotated tag before routine progression or later evidence exposure.
metadata:
  category: discipline
  triggers: freeze research stage, lock experiment, git evidence tag, MLH checkpoint, advance stage
---

# Freeze a research boundary

Freezing preserves evidence; it does not certify correctness.

## Preconditions

1. The user requested a freeze/stage advance, or a recorded prior authorization explicitly covers routine freezes within this route. Do not ask twice for the same authorized action.
2. [Status](../mlh-status/SKILL.md) verifies applicable prerequisites using [research-contract.md](../mlh/references/research-contract.md) and [artifact-contract.md](../mlh/references/artifact-contract.md).
3. The current stage is substantive; required checkpoint reviews and actual decisions are present. Formal data/develop need review before outer exposure, outer evidence before confirmatory conclusion, and final evidence/monitoring before deployment advancement. Reviews may be combined; not every intermediate freeze needs a new signature.
4. Repository, exact commit scope, exposure ancestry, and procedure identity are known.

## Workflow

1. Inspect Git status, existing tags, evidence and declared `implementation_paths`; preserve unrelated work.
2. Stage only the exact study artifacts and reproduction paths. Include `exposure.yaml` and immutable ancestor references, not secrets or blindly copied datasets.
3. Inspect the cached diff and run `git diff --cached --check`; reject placeholders and unrelated files.
4. Commit with `mlh(<stage>): <study-id>` and create annotated tag `mlh-<stage>-<study-id>` pointing to that exact commit.
5. Verify annotation, commit contents and required identities, then report both.

Follow the level-dependent route. A formal not-applicable impact needs a report and boundary; a predeclared optional holdout needs no empty freeze. A pilot snapshot is permitted but is not formal validation. Never delete or move an existing evidence tag to hide corrections. New revisions preserve ancestor exposure; frozen rolling rules permit subsequent scheduled fits without retagging the procedure after each fit.
