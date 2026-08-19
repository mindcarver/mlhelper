---
name: mlh-impact
description: >-
  Use when translating locked ML predictions into decisions, rankings, policies, simulations, backtests, interventions, costs, capacity, harms, or other downstream impact evidence.
metadata:
  category: technique
  triggers: model impact, decision policy, backtest, cost benefit, offline policy evaluation, simulation
---

# Validate downstream impact

Prediction quality and decision value are separate claims.

## Gate

The test stage must be closed and frozen or otherwise immutably identified. The prediction-to-decision policy, constraints, cost model, impact metrics, and sensitivity ranges must be declared before impact outcomes are viewed. If test evidence was used to design them, create a new revision rather than treating impact as independent evidence.

## Route by decision

- Trading or allocation: positions, latency, turnover, fees, slippage, capacity, exposure, drawdown, concentration.
- Classification intervention: threshold, action cost, false-positive/negative harm, capacity, fairness, deferral, calibration.
- Ranking or recommendation: cutoff, exposure policy, utility, diversity, feedback effects, coverage.
- Forecast-driven planning: decision rule, asymmetric cost, resource constraints, scenario sensitivity.
- No downstream action: write `not_applicable`, explain why, and limit the conclusion to predictive performance.

## Workflow

1. Verify the locked recipe and policy identities.
2. Simulate only information and actions available at decision time.
3. Report gross model performance separately from costs, risks, harms, and net impact.
4. Stress predeclared assumptions and show which ones dominate the conclusion.
5. Check concentration by entity, period, group, and extreme event.
6. Write `impact/impact-report.md`; record both supporting and counter-evidence.

Do not tune the model or decision policy on impact outcomes. A better threshold discovered here is a hypothesis for a new revision.
