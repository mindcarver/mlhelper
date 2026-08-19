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
