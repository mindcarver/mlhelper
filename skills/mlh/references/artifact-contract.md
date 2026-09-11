---
description: Lists MLH evidence artifacts, level-dependent completion, and legacy compatibility.
metadata:
  tags: artifacts, completion criteria, study workspace, evidence
---

# Artifact contract

Use `studies/<study-id>/`, or map equivalent paths explicitly in `study.yaml`.

```text
study.yaml
RESEARCH.md
exposure.yaml
data/{data-card.md,split-manifest.yaml,leakage-audit.md}
develop/{baselines.csv,experiments.csv,selection.md,recipe.yaml}
test/test-report.md
impact/impact-report.md
holdout/holdout-report.md
reviews/
```

Large data, predictions, and model artifacts may live outside Git. Record immutable URIs, versions, hashes, and generation code. A path alone is not an immutable identity.

## Shared requirements and levels

Apply [research-contract.md](research-contract.md) for validation levels, exposure, review checkpoints, and authorization. Exploratory pilots may keep substantive framing, data provenance, attempts, and findings in `RESEARCH.md` alongside `study.yaml` and `exposure.yaml`; map any combined artifacts explicitly. Do not create empty stage reports to appear complete. For formal studies use the artifacts below. Required stages are determined by the recorded plan, not file existence.

`exposure.yaml` records dataset identity and overlap, disclosure policy, selector access history, current eligibility, and inherited ancestor events. Its `history_status` must be `reconstructed` before claiming independent evidence. An empty event list alone is not proof of untouched data; record the access-control evidence and responsible custodian. A rejected access attempt with no disclosure is not exposure but may be logged separately in the research record.

## frame and feasibility

- Provisional exploration identifies the question, development-only data, provisional target/unknowns, scope, and pilot budget; researcher authorization to explore is recorded. Log exploratory choices and failed attempts.
- Formal `study.yaml` contains a substantive target, decision timestamp/context, hypothesis and counter-hypothesis, scope, kill criteria, metrics/uncertainty, baselines, search budget, split roles, validation level, final-evidence plan, reviews, and decisions.
- `RESEARCH.md` distinguishes exploration from the subsequent formal protocol and links its immutable boundary. Exploration-influenced data remains development evidence.

## data

- `data-card.md`: source/access constraints, entity and time keys, population, exclusions, development missingness and target distributions, snapshot identity.
- `split-manifest.yaml`: immutable membership or deterministic rules, grouping, label availability/horizon, overlap purge/gap, seed, and allowed structural disclosures; record how test and impact datasets/predictions relate.
- `leakage-audit.md`: availability, duplicates, overlap, revisions, preprocessing, target proxies, access controls, and any deferred sealed checks. Do not publish sealed outcome statistics into these reports.
- Sample adequacy uses development estimates and predeclared structural information or a sealed check; missing sealed outcome details are not a reason to open labels early.

## develop

- `baselines.csv`: applicable naive, simple, incumbent, and decision-policy baselines.
- `experiments.csv`: every influential pilot/formal trial or a linked pilot log, identity, fold metrics, uncertainty, status/rejection, and compute cost. Selection budget accounts for manual trials and inherited attempts; state any approved new revision budget without erasing cumulative counts.
- `selection.md`: stability, ablations, negative controls, policy/cost tradeoffs, uncertainty, and selection justification.
- `recipe.yaml`: complete frozen learning and decision procedure. Identify data/splits, feature availability, fold-fitted preprocessing, model/parameters, seeds, calibration/threshold/policy, costs, code/dependencies, and immutable prediction outputs when generated.
- For fixed models identify the fitted artifact and training membership. For rolling procedures additionally identify training window, schedule, label maturity, allowed past evaluation observations, feature/parameter search rules and per-update budget, calibration/policy updates, execution lag, unavailable-data fallback, and per-step logs. Specify `not_applicable` with a reason for irrelevant fields. Freeze selection rules, not future unknowable fitted weights.

## test

- The evaluated procedure matches frozen develop identities and eligible evidence.
- `test-report.md`: predeclared endpoints, uncertainty suitable for dependencies, baseline deltas, subgroup/time stability, failures, first exposure timestamp, and prediction artifact identity.
- Rolling evaluations record each fit cutoff, eligible label times, fitted artifact, and prediction/decision time; no outcome-driven manual change or favorable rerun selection.
- Distinguish post hoc diagnostics from predeclared endpoints and preserve failures.

## impact

- `impact-report.md`: locked prediction-to-decision policy, costs/capacity/latency/harms/risk, net consequences, predeclared sensitivity, and supporting/counter-evidence.
- Identify datasets and prediction artifacts shared with test. Shared samples are not an independent replication.
- No downstream claim: explicit `not_applicable` reason and a corresponding claim limit. Exploratory-only studies may skip formal test/impact reports entirely.

## final evidence (holdout or prospective)

- The plan was fixed before outcomes were opened (before future outcomes accrued for prospective evidence); access history supports untouched eligibility.
- Test/impact are immutable and their decisions closed under recorded authorization; the final-opening decision is recorded.
- `holdout-report.md`: evidence mode, exact procedure/policy, first exposure, predictions, decay/direction/stability/uncertainty/failures and, for rolling evaluation, per-step identities. No redesign.
- `validation.final_evidence: none` permits skipping this stage only for exploratory/confirmatory plans. A deployment study lacking final evidence is incomplete for advancement, though an early limited conclusion is allowed.

## conclude

- `RESEARCH.md`: claim-evidence map, observation vs inference, limitations, counter-evidence, review resolution, original plan vs achieved evidence, and one researcher decision: stop, revise, monitor, or advance.
- Confirmatory evidence can support the stated claim without a second holdout if the plan specified `none`; never claim final holdout support that does not exist.
- Deployment advancement also requires a named next step and a monitoring plan: owner, cadence, observable data/performance/decision-cost checks, delayed-label handling, stop/rollback criteria, and action authority. Recording a plan does not start a service or execute trades.

## Version 1 studies

New templates use `schema_version: 2`. Reading version 1 is supported as a legacy record: keep its original route and evidence requirements (including its originally required final holdout); do not silently assign a lighter level, infer untouched status, or mark it complete.

`mlh-status` reports absent level, exposure, procedure, and governance fields as missing/unverified without editing. On an authorized update, reconstruct them from actual records, preserve immutable originals, and log the migration. Pure metadata mapping with unchanged predictions, samples, and claims may stay in the same revision. Any material redesign or post-exposure relaxation needs a linked revision with inherited exposure; a schema bump alone cannot repair invalid evidence. Unknown historical access remains unknown.
