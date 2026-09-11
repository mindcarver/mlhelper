---
name: mlh-impact
description: >-
  Use when translating locked ML predictions into decisions, rankings, policies, simulations, backtests, interventions, costs, capacity, harms, or other downstream impact evidence.
metadata:
  category: technique
  triggers: model impact, decision policy, backtest, cost benefit, offline policy evaluation, simulation
---

# Validate downstream impact

Predictive quality and decision value are distinct claims; both can be evaluated on shared evidence.

## Gate

Read [research-contract.md](../mlh/references/research-contract.md). Formal test is closed and immutable. Policy, cost model, constraints, metrics, and sensitivity ranges were developed inside training validation and locked before test exposure. If test influenced redesign, create a linked revision with inherited exposure; do not relabel reused outcomes as independent evidence.

Exploratory policy experiments belong in develop. No downstream action permits an explicit `not_applicable` report with a reason; no financial metric needs to be invented.

## Workflow

1. Verify frozen procedure, policy, data, and prediction identities. Declare whether samples/predictions are shared with test. Shared evidence supports different endpoints, not independent replication; separate datasets also need dependence checks.
2. Simulate only information and actions available at each decision time. Preserve the rolling execution provenance if applicable.
3. Apply the domain-relevant constraints:
   - trading/allocation: latency, turnover, fees, slippage, capacity, exposure, drawdown, concentration;
   - intervention: action cost, asymmetric harm, capacity, fairness, deferral, calibration;
   - ranking: cutoff, exposure, utility, diversity, feedback, coverage;
   - planning: asymmetric cost, resource constraints, scenario sensitivity.
4. Separate prediction metrics from costs, risks, harms, and net consequences; stress only predeclared assumptions for confirmatory claims.
5. Check concentration across entities, time, groups, and extreme events. Label additional diagnostics post hoc.
6. Write [impact artifacts](../mlh/references/artifact-contract.md), supporting/counter-evidence and actual decisions under the declared authorization.

Do not tune the model, threshold, policy, cost model, or excluded samples on impact outcomes. A promising modification is a revision hypothesis with the same inherited exposure history.