---
name: mlh-conclude
description: >-
  Use when synthesizing completed ML evidence into supported claims, limitations, boundary conditions, a stop-or-revise decision, or a recommendation to monitor or advance.
metadata:
  category: technique
  triggers: conclude ML study, research verdict, evidence synthesis, model recommendation, negative result
---

# Conclude from the evidence

State what the evidence supports and which planned requirements remain unmet.

1. Use [status](../mlh-status/SKILL.md) read-only. Apply [research-contract.md](../mlh/references/research-contract.md) and [artifact-contract.md](../mlh/references/artifact-contract.md).
2. Reconstruct the original question, validation level, final-evidence plan, hypothesis/counter-hypothesis, criteria and budget without rewriting them to fit results.
3. Map claims to predictive quality, decision value, uncertainty, baseline increments, stability, counter-evidence and reviews. Count shared test/impact outcomes once as evidence, not two independent replications.
4. Separate observations, statistical inferences, mechanism speculation and operational assumptions. State boundaries by population, time, regime, label availability, and fixed/rolling procedure.
5. State achieved support: exploratory, test-supported, impact-supported, or final-evidence-supported. Confirmatory can conclude without extra holdout when the original plan specified none. Missing required final evidence prevents claiming completion/advancement at deployment level. Early stop or inconclusive conclusions remain valid and list incomplete stages.
6. Record one actual researcher-approved decision:
   - `stop`: negative, invalid, or not worth continuing;
   - `revise`: linked new design with inherited exposures and a valid new-evidence plan;
   - `monitor`: prospective observation needed; record the proposed plan without starting an automation;
   - `advance`: evidence supports an explicitly named next step, not blanket deployment permission.
7. For deployment advancement verify final review and a monitoring plan covering owner, cadence, delayed labels, data/performance/cost checks, stop/rollback criteria, and authority.
8. Update the Conclusion in `RESEARCH.md` only when asked to record a supplied/authorized decision. Never invent the researcher's judgment.

Preserve negative and inconclusive studies. No causal claim follows solely from predictive performance or feature importance. New ids, schema migrations, or level downgrades do not erase exposed data or failed requirements.