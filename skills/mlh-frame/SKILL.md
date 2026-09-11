---
name: mlh-frame
description: >-
  Use when a predictive ML idea needs bounded development-data feasibility, a formal protocol, validation level, or a revision with inherited evidence exposure.
metadata:
  category: technique
  triggers: frame ML study, research question, prediction target, success criteria, new ML experiment
---

# Frame an ML study

Create a useful provisional question, then a falsifiable formal protocol.

## Workflow

1. Locate the intended study root. Discussion alone does not authorize file creation. Read [research-contract.md](../mlh/references/research-contract.md) and check known ancestor/data exposure before choosing evidence.
2. Establish the predictive task and intended decision, population, observation unit, prediction timestamp, provisional target/horizon, and unknowns. Do not invent an unconfirmed target silently.
3. If feasibility is requested, designate development-only data and a small time/trial budget. Inspect availability, provisional labels, sample sufficiency, and a cheap baseline through data/develop as needed. Record influential attempts and assumptions in `RESEARCH.md` and `exposure.yaml`; complete formal framing is not a prerequisite for this pilot.
4. For formal research choose `validation.level`, justify `validation.final_evidence`, and define hypothesis, counter-hypothesis, kill criteria, metrics/uncertainty, baselines, split family, search limits, selection rules, and impact protocol. Consult [split-protocols.md](../mlh/references/split-protocols.md) for dependencies.
5. Declare the complete fixed or rolling learning/decision procedure, including how policy selection will occur inside development; no need to know future fitted weights at framing.
6. Record review checkpoints and actual researcher authorization scope. Freeze substantive frame and data before formal development. Do not use test/holdout outcomes to set the protocol.
7. On an authorized new study, instantiate [study.yaml](../mlh/assets/study.yaml), [RESEARCH.md](../mlh/assets/RESEARCH.md), and [exposure.yaml](../mlh/assets/exposure.yaml). For revisions set a new id, parent and reason, and inherit ancestor exposure and cumulative attempts with immutable references. Missing history is unverified, never untouched.
8. Apply [artifact-contract.md](../mlh/references/artifact-contract.md) for version 1 migration; do not rewrite frozen history or silently relax requirements.

## Quality checks

Formal questions name what is predicted, for whom, when, and for which decision. Active search needs a positive budget; placeholders do not count as a protocol. Development exploration can inform the protocol but cannot later become independent evidence. End with unresolved assumptions and the smallest next action within the request.
