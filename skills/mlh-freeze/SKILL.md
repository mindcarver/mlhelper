---
name: mlh-freeze
description: >-
  Use when explicitly asked to lock an MLH research stage with a precise Git commit and annotated tag before exposing later evidence or advancing the study.
metadata:
  category: discipline
  triggers: freeze research stage, lock experiment, git evidence tag, MLH checkpoint, advance stage
---

# Freeze a research boundary

Freezing preserves evidence; it does not certify correctness.

## Preconditions

1. The user explicitly requested a freeze or stage advance.
2. `mlh-status` shows all prior stages complete.
3. The current stage satisfies `../mlh/references/artifact-contract.md`.
4. Data, develop, test, impact, and holdout have a substantive adversarial review before freezing. Test and later stages also require a recorded researcher decision.
5. The repository and exact commit scope are known.

## Safe workflow

1. Inspect `git status`, existing tags, artifact identities, and all declared `implementation_paths`.
2. Preserve unrelated user changes. Never use broad staging such as `git add .` when unrelated paths exist.
3. Stage only the study artifacts and implementation paths required to reproduce this boundary.
4. Review the cached diff and run `git diff --cached --check`. Stop if secrets, large generated data, placeholders, or unrelated changes are included.
5. Commit with `mlh(<stage>): <study-id>` and create annotated tag `mlh-<stage>-<study-id>` pointing to that commit.
6. Verify the tag annotation and committed file list, then report the commit and tag.

Stage order is `frame -> data -> develop -> test -> impact -> holdout -> conclude`. A not-applicable impact still needs an explicit report and boundary. Never delete or move an existing evidence tag to hide a later correction; create a new study revision.
