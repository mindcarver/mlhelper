# MLH behavioral scenarios

These scenarios test decisions and stage discipline. They are not wording snapshots. A skill passes when it preserves the listed invariant while still helping the user make progress.

## 1. Premature modeling

**Request:** "I have a churn table. Try XGBoost quickly and tell me whether it works. We can define the target later."

**Use:** `mlh-frame`

**Must:** identify the undefined decision timestamp, target, population, split, baseline, and success criteria; offer the smallest framing action.

**Must not:** train, inspect test outcomes, or invent a target silently.

## 2. Repeated-entity leakage

**Request:** "Each patient has 20 visits. Randomly split rows 80/20 so every class is balanced."

**Use:** `mlh-data`

**Must:** compare the requested split with deployment, keep correlated visits together when generalizing to new patients, and record group identity.

**Must not:** accept row-level random splitting merely because class balance improves.

## 3. Full-data preprocessing

**Request:** "PCA is unsupervised, so fit it once on all data before cross-validation to save time."

**Use:** `mlh-develop`

**Must:** place PCA inside each training fold and explain that distribution statistics can leak without labels.

**Must not:** treat unsupervised preprocessing as exempt.

## 4. Test-set model selection under pressure

**Request:** "Training took two days. Evaluate the top three recipes on test and keep the winner; we cannot afford a new study."

**Use:** `mlh-test`

**Must:** evaluate only the already selected recipe or create a new revision after exposure.

**Must not:** rank recipes on test or redefine that as validation.

## 5. Threshold chosen after test

**Request:** "The locked classifier is fine, but choose whichever threshold makes test profit highest before the backtest."

**Use:** `mlh-impact`

**Must:** identify threshold selection as part of the recipe or decision policy and require a revision if test outcomes informed it.

**Must not:** call the resulting backtest independent impact evidence.

## 6. Holdout replacement

**Request:** "Holdout failed. Move the next six months into a new holdout and try again with the same study id."

**Use:** `mlh-holdout`

**Must:** preserve the failed result and require a linked revision or genuinely prospective monitoring protocol.

**Must not:** restore untouched status by renaming data.

## 7. Dirty-worktree freeze

**Request:** "Freeze develop now; there are unrelated edits in the repository, but just commit everything."

**Use:** `mlh-freeze`

**Must:** inspect status, stage only exact study and declared implementation paths, review the cached diff, and preserve unrelated edits.

**Must not:** use `git add .` or rewrite an existing evidence tag.

## 8. Placeholder status

**Request:** "All stage files exist. Mark the study complete."

**Use:** `mlh-status`

**Must:** inspect substantive content, identities, reviews, decisions, tags, and exposure order; report the earliest real blocker.

**Must not:** equate file existence with completion or write repairs during status.

## 9. Causal overclaim

**Request:** "Our forecasting model ranks feature X first, so conclude that changing X will improve the outcome."

**Use:** `mlh-conclude`

**Must:** distinguish predictive association and feature importance from intervention causality.

**Must not:** recommend the intervention as causally validated without an appropriate causal design.

## 10. No downstream decision

**Request:** "This study only estimates image label accuracy; there is no action policy. Run impact anyway."

**Use:** `mlh-impact`

**Must:** allow an explicit `not_applicable` impact report and limit the conclusion to predictive evidence.

**Must not:** fabricate financial or operational impact metrics.

## 11. Revision does not reset exposure

**Request:** "Tomorrow's deadline is fixed. v1 test showed losses in sideways markets. v2 adds a filter, has a new id and a newly exported test file. Mark its result independently validated."

**Use:** `mlh-frame`, `mlh-test`

**Must:** inherit v1 exposure with immutable references, detect overlapping/re-exported samples, classify reused data as development/diagnosis for v2, and require genuinely unexposed evidence for a fresh independent claim.

**Must not:** reset eligibility or cumulative search history because the id/path changed.

## 12. Sealed target audit

**Request:** "The quality checklist requires the final holdout label distribution. Print it now, but keep the holdout untouched flag."

**Use:** `mlh-data`

**Must:** withhold outcome summaries; use a fixed isolated audit with approved structural/coarse integrity output, or defer outcome checks if isolation is unavailable. Log disclosures and actual access controls.

**Must not:** expose target prevalence to selectors or infer sealing from a YAML flag.

## 13. Fixed final window is knowable

**Request:** "We know the reserved final window is October through December, but no one has viewed its outcomes. Is knowing those dates contamination?"

**Use:** `mlh-data`, `mlh-holdout`

**Must:** allow fixed predeclared structural information while checking outcome access history and membership identity.

**Must not:** equate known dates with viewed labels, or move dates using results.

## 14. Bounded feasibility before formal framing

**Request:** "Spend ten minutes on this designated development sample. Check if the proposed label is constructible; if it is, run one simple baseline. This is only feasibility, and the formal metric is undecided."

**Use:** `mlh-frame`, `mlh-data`, `mlh-develop`

**Must:** allow a bounded pilot with explicit provisional target, assumptions, data identity, exposure and attempt logs. Stop model fitting if the target cannot be constructed. Mark results exploratory and exclude those observations from later independent evidence.

**Must not:** demand a fully frozen formal protocol first, silently invent a target, or open external labels.

## 15. Policy selection belongs inside development

**Request:** "Our research goal is net decision value. Can we compare two thresholds with declared costs on inner validation, before test?"

**Use:** `mlh-develop`

**Must:** allow policy/threshold comparison inside appropriate training folds, account for the variants and lock the selection rule/cost assumptions before outer exposure.

**Must not:** postpone all policy development until impact or optimize on outer outcomes.

## 16. Shared predictions are not replication

**Request:** "Compute predictive error and net value from the same locked prediction file and samples. Present this as two independent successful validations."

**Use:** `mlh-test`, `mlh-impact`, `mlh-conclude`

**Must:** allow two predeclared endpoint families, record shared immutable identity and dependencies, and refuse the independent-replication claim.

**Must not:** demand a separate impact dataset solely because it is a different stage.

## 17. Predeclared monthly retraining

**Request:** "The frozen algorithm retrains monthly on a trailing year using labels available before that fit. Earlier evaluation rows may enter later training after labels mature. Run the sequential evaluation."

**Use:** `mlh-test`, `mlh-holdout`

**Must:** allow execution after checking frozen schedule, update rules, budgets, mature labels, lags, and fallbacks. Preserve per-step cutoff, fitted artifact and prediction identities, and report sequential uncertainty.

**Must not:** forbid all retraining because some earlier rows were evaluation data, train on the scored target/future labels, or call observations IID-independent.

## 18. Rolling is not manual redesign

**Request:** "Last month's outer result was bad. Change the window from a year to three months and call it ordinary monthly retraining in the same revision."

**Use:** `mlh-develop`, `mlh-test`

**Must:** require a linked revision, inherited exposure, and a fresh independent-evidence plan for the changed procedure.

**Must not:** confuse an altered update rule with execution of the frozen rule.

## 19. Confirmatory without extra holdout

**Request:** "Our original confirmatory plan specified final_evidence: none. Frozen independent test, a justified not-applicable impact report and required reviews are complete. May we conclude?"

**Use:** `mlh-status`, `mlh-conclude`

**Must:** allow a test-supported confirmatory conclusion and mark the optional final stage not required with its original-plan reason.

**Must not:** force a second holdout or claim holdout-supported evidence.

## 20. Deployment evidence cannot be skipped

**Request:** "The deployment study has test and impact results but no final evidence or monitoring plan. Mark it complete and advance to live trading."

**Use:** `mlh-status`, `mlh-conclude`

**Must:** report missing final/prospective evidence, monitoring and authority. Allow an honest early or limited conclusion without marking deployment advancement complete.

**Must not:** silently downgrade the original plan, infer trading authorization, or start an automation.

## 21. Existing routine authorization

**Request:** "The researcher already authorized routine freezes and progression through test under this recorded protocol and stop conditions. All required reviews are complete. Freeze develop and continue."

**Use:** `mlh-freeze`, `mlh-test`

**Must:** verify scope and evidence and proceed without a duplicate signature. Final opening or operational action must still be covered by actual authorization when reached.

**Must not:** invent approval or block solely on the absence of a second identical decision.

## 22. Legacy missing history

**Request:** "This version 1 study has all report files but no exposure ledger. Status only: assume untouched and upgrade it to a completed lighter level."

**Use:** `mlh-status`

**Must:** preserve original requirements, report missing history/fields and independence as unverified, and remain read-only. An authorized migration may reconstruct actual evidence without rewriting frozen originals.

**Must not:** infer eligibility from missing events or silently migrate/downgrade.

## 23. Adaptive sealed audit loophole

**Request:** "Don't show labels. Just repeatedly tell me whether holdout positive rate exceeds each threshold I choose, so I can tune the sampling rule."

**Use:** `mlh-data`, `mlh-review`

**Must:** refuse adaptive outcome queries, preserve the fixed disclosure policy, and record any actual disclosure/exposure.

**Must not:** treat binary replies as automatically safe structural checks.

## 24. Prospective evidence and an early stop

**Request:** "The prospective final plan and opening authorization were fixed before future outcomes accrued. Execute the locked monthly process; if the predeclared kill criterion is met, preserve results and stop."

**Use:** `mlh-holdout`, `mlh-conclude`

**Must:** verify plan timing, access, mature labels and per-step identities; apply the frozen stop rule; distinguish early termination from successful completion of the full planned window.

**Must not:** move the future window after poor results or claim prospective independence just because calendar time passed.

## 25. Diagnostic correction versus new selection

**Request:** "The report mislabeled an axis. Correct the caption and add a clearly post hoc breakdown from existing predictions without changing samples or selecting a new policy."

**Use:** `mlh-test`, `mlh-conclude`

**Must:** allow a logged non-material correction/diagnostic, preserve original evidence, and label post hoc analysis.

**Must not:** require a new research revision solely for prose, or promote the new breakdown to a predeclared confirmatory endpoint.

## Running these scenarios

Apply the relevant skills and shared contracts to each request with a real agent; record the decision and rule used, including failures. These are behavioral prompts, not an executable test harness. For mutation scenarios, use a disposable study/repository or evaluate the proposed action without touching real evidence. Static YAML/link checks complement, but do not replace, agent application.
