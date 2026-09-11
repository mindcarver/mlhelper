---
description: Defines MLH exploration, evidence boundaries, revision inheritance, and validation levels.
metadata:
  tags: research governance, exposure, revisions, validation
---

# Research contract

## Research path

```text
provisional frame <-> development-data feasibility
        -> formal frame -> data -> develop -> test -> impact -> holdout -> conclude
```

Feasibility belongs to frame/data, not a new skill. Before exploration, identify a provisional question, a development-only dataset, its known exposure history, and the limits of the intended claim. Inspect labels, build a provisional target, and run a cheap baseline only on that development data when exploration is requested. Log choices and attempts, including failures. Do not silently invent a target. Freeze the substantive protocol and data rules before formal model selection or opening outer outcomes. Development-data findings may inform that protocol.

The development loop includes baselines, features, preprocessing, models, calibration, decision rules, costs, inner validation, ablation, and selection. All selection stays inside training data. Formal outer evaluation tests a locked learning and decision procedure.

## Validation levels

Choose and justify `validation.level` before formal development. Integrity rules apply at every level; levels change required evidence, not what counts as leakage.

| Level | Required route | Claim boundary |
|---|---|---|
| `exploratory` | Provisional frame/data, develop as needed, conclude | Feasibility and selection evidence only; no independent-performance claim. Formal protocol freeze is not required for a bounded pilot. |
| `confirmatory` | Formal frame, data, develop, independent test, impact report, conclude | Independent evaluation of a predeclared claim. Impact may be explicitly not applicable. An extra holdout is optional unless predeclared. |
| `deployment` | Confirmatory route plus untouched final holdout or predeclared prospective validation, then conclude | Evidence for a named next operational step; also requires monitoring and exit rules. MLH does not authorize or execute deployment. |

Record the final-evidence plan as `validation.final_evidence: none | holdout | prospective`. Exploratory uses `none`; confirmatory can use any option; deployment cannot use `none`. Prospective final evidence is evaluated by `mlh-holdout` using a plan fixed before future outcomes accrue, with the same exposure and no-redesign rules. A requested, predeclared final evaluation cannot be dropped after poor results; stop or conclude with that limitation. Early stop or inconclusive conclusions are valid at any level and list unmet requirements; they do not mark the planned route complete.

`review` may challenge any stage; `status` is read-only; `freeze` preserves an immutable boundary, not a certificate of correctness. Formal frame and data must be immutable before formal develop; develop must be immutable before test, test before impact, and test/impact decisions before final evidence. A boundary may be an exact Git commit/tag or an equally reproducible immutable manifest. A passing metric never substitutes for evidence review.

## Exposure and access

Evidence is exposed when anyone selecting the procedure inspects labels, target summaries, metrics, outcome-bearing charts, predictions, or qualitative outcomes. Record the first such access, even when the result did not improve the model. An explicit predeclared structural disclosure is not outcome exposure: for example schema, fixed time ranges, snapshot hashes, or a coarse integrity check. Unknown history means independence is unverified, not untouched.

Use `exposure.yaml` to track immutable dataset identities, overlapping populations/windows, access roles, allowed disclosures, exposure events, and current claim eligibility. If a dataset is renamed, re-exported, or partly overlaps known exposed data, preserve that history. Permission boundaries must be real where sealed access is claimed; a YAML flag does not prevent an agent from reading files.

| Role | Allowed audit before evaluation |
|---|---|
| Development | Full exploratory access; never later claim these observations are independent evidence. |
| Test | Predeclared structural/integrity information; no outcome summaries or predictions to selectors before lock. |
| Final holdout / prospective | Fixed membership rules/time range and snapshot identity may be known. Seal labels, target statistics, predictions, and outcomes until the final gate. |

If sealed data needs quality checks, use an isolated custodian or process following fixed checks and a fixed disclosure policy. It may release only approved non-outcome structural information or a coarse integrity pass/block, not target prevalence, performance, or outcome-driven reasons. Log disclosures. Do not adapt checks or boundaries through repeated pass/block queries. If isolation is unavailable, defer the outcome-sensitive audit until authorized exposure or record the exposure and loss of untouched status. Sample adequacy planning uses development estimates or a sealed fixed check, not disclosed holdout target distributions.

## Revision inheritance

A new revision has a new id, `revision.parent_id`, and `revision.reason`, and preserves parent evidence. It MUST inherit all known ancestor exposure events and any other known exposure relevant to selectors, with immutable source references. Copying a new id, tag, seed, data path, or split name never restores independence. Missing parent history blocks independent claims until reconstructed.

Data that informed any ancestor's or current selector's design can support development or diagnosis, but not a fresh independent estimate for the revised procedure. Use genuinely unexposed data, a predeclared future evaluation, or conclude with the limitation. Track cumulative attempts across revisions; restarting the trial counter does not erase selection multiplicity. Repeatedly seeking successful independent tests still requires disclosure of all attempts and appropriate uncertainty/claim limits.

## Material changes and permitted execution

After outer exposure, changes that can alter predictions, samples, selection, or the claim require a linked revision: features, label fixes, preprocessing, parameters, seed policy, exclusions, thresholds, ensembles, costs, retraining schedule, or primary metrics. New diagnostics from locked outputs and prose/reporting corrections are allowed when they do not select a new procedure or retrospectively become confirmatory endpoints. Record them as post hoc.

A locked procedure can be either a fixed fitted model or a predeclared rolling learning algorithm. Scheduled retraining is execution, not redesign, only when all windows, label-availability rules, parameter/feature-selection rules, calibration, decision updates, randomness, and fallback behavior were fixed beforehand. At each prediction time use only data and labels then available; a matured earlier evaluation observation may enter a later scheduled training window if explicitly predeclared. Never fit on the observation being scored or future labels. Such evaluation estimates sequential performance of the locked algorithm, not performance of one unchanged fitted model or IID-independent rows.

Unplanned manual adjustments after viewing results require revision. An operational retry with no changed procedure or outcome-guided selection may resume from preserved state and logs; preserve failures and existing exposure, never rerun to choose favorable stochastic results.

## Test and impact

Test measures predictive performance; impact measures the predeclared prediction-to-decision consequences. Develop the policy and cost assumptions inside inner validation, then lock them before test exposure. Test and impact may share an immutable prediction artifact and samples or use distinct declared datasets. Record which. Shared data means two endpoints on the same evidence, not two independent replications. Distinct datasets still require dependency and exposure checks before independence claims.

No downstream claim allows `impact: not_applicable` with a reason. Do not disguise prediction metrics as impact. If downstream value is the primary claim, predeclare the selection/evaluation metrics accordingly; do not introduce an arbitrary predictive-score gate after results are known.

## Review, decisions, and stopping

Declare `governance.review_checkpoints` and researcher decision checkpoints. Formal studies require substantive review of data/develop before outer exposure, and of outer evidence before a confirmatory conclusion. Deployment additionally requires final evidence and monitoring review. Reviews can cover several stages in one document, linked to the exact identities. Explicit freezes of intermediate reports need completion evidence, not a new human signature at every stage.

Record actual researcher decisions on the goal/protocol, material revision, final-evidence opening, and conclusion/operational next step. Prior explicit authorization may cover routine execution through the declared route; record its scope and stop conditions. Never invent approval, and never reinterpret research authorization as permission to deploy. Freeze or ordinary stage transitions within that scope need no duplicate approval. Blocking integrity findings stop progression; uncertainty may support stop, revise, monitor, or a limited conclusion without rewriting criteria.

Stop for leakage, invalid timestamps, exhausted budget, kill criteria, or missing independent evidence required by the intended claim. Preserve negative results. Reducing the validation level after exposure cannot rescue a failed confirmatory claim; retain the original plan and record the weaker conclusion explicitly.
