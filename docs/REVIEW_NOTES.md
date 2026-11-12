# Review before public release

## Evidence discrepancies

- The report abstract describes over 80,000 records. Saved notebook outputs show 40,875 loaded and retained records. The attached CSV contains 910,707 rows. The notebook has no initial 40,875-row selection step to explain this difference.
- The saved phase counts include 31,417 lockdown and 9,458 pre-lockdown records, with no post-lockdown category shown. They do not substantiate a post-lockdown rebound.
- The code filter is 2020-01-01 to 2023-06-19. The attached CSV has no 2019 occurrences. Avoid describing this implementation as a 2019–2023 analysis.
- The report abstract gives XGBoost accuracy 0.9565; the saved notebook gives approximately 0.947566. Establish which data/run produced the report figures.

## Methodological review

- Imputation, encoding, scaling and SMOTE occur before GridSearchCV. Validation folds therefore are not isolated from preprocessing/resampling. Move these steps into a pipeline fitted within each fold. This concern applies to the reported cross-validation scores; it does not by itself prove the separate test set was used for training.
- Plain SMOTE interpolates ordinal-encoded categories into fractional values. Consider class weighting or a correctly configured categorical-aware method such as SMOTENC within folds.
- The list defining violent crime is project-specific and needs a documented rationale. Unmatched descriptions default to non-violent, including potentially missing or unrecognised categories.
- Zero victim age is currently classified as Child. Verify source coding for unknown age and handle accordingly.
- Weapon description and other recorded attributes may reveal offence characteristics unavailable before the incident. Frame the task as retrospective classification and inspect feature sensitivity.
- Raw phase totals cover unequal durations. Compare counts per unit time and document the rationale for phase boundaries.
- A random split does not establish future-period performance. Consider a temporal holdout for claims of generalisation over time.
- Use an untouched final test set, uncertainty estimates and sensitivity analyses; avoid causal claims from descriptive trends alone.

## Preparation changes and validation

Only the notebook loading path, introductory note, output clearing and runtime metadata were changed. Original modelling logic is retained. Code cells passed Python syntax parsing. Full training was not run; dependencies are unpinned and untested. Neither the original report nor presentation has been edited or included. The report text was inspected to identify the differences above.

Recommended next action: confirm the intended data snapshot and selection, then correct validation and rerun. Preserve any revised analysis as an explicitly documented revision of the submitted work.
