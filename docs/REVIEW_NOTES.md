# Methods and remaining review items

## What this package contains

The author's completed 13 November 2026 Colab rerun of the original dissertation
workflow, with saved results and figures. The full input contains 910,707 records;
filtering produces 750,936 study-period records. Models are fitted on a 10,000-row
training sample, expanded to 14,376 rows by SMOTE. The test set has 225,281 original
records. The original code does not train models on all study-period records.

The optional revised model-validation script is not used in this package.
This package preserves the original modelling method and its current results.

## Validation limitations

1. **Preprocessing and resampling precede cross-validation.** Imputation, ordinal encoding, scaling and SMOTE are fitted/applied before GridSearchCV. Validation folds are therefore not fully isolated during model selection. A future methodological revision should fit these steps within each training fold using an appropriate pipeline. The original test set is separately held out and is not resampled; the CV limitation does not by itself prove direct test-set contamination.
2. **Ordinary SMOTE treats ordinal category codes as numbers.** Interpolation can create invalid fractional category codes and fractional calendar features. Consider categorical-aware sampling or class weighting in a separate, documented revised experiment.
3. **The label definition is project-specific.** Offence descriptions in the manual list are positive; unmatched descriptions become negative. Review the list and treatment of missing descriptions before making general criminological claims.
4. **Age zero is currently assigned to Child.** Verify the provider's coding for missing or unknown victim age and any valid age-zero records before changing that rule.
5. **The split is random, not temporal.** This experiment does not demonstrate performance on a genuinely future period. Attributes such as weapon description may only be available after an incident.
6. **No uncertainty or significance test is provided.** XGBoost and Random Forest are close in this run. Their score difference does not establish reliable superiority.

## Descriptive interpretation

- The phase boundaries are the project's operational definitions, not a validated representation of every restriction in force.
- The phases last 78, 319 and 869 calendar days. Raw totals mainly reflect both duration and incident frequency; daily averages provide a clearer descriptive comparison.
- June 2023 ends on 19 June. The final monthly point covers an incomplete month.
- Recorded incidents do not capture all underlying crime. Reporting and recording behaviour may change.
- These descriptive associations do not establish that lockdowns caused changes in crime.

## Written report reconciliation

The submitted report's abstract describes over 80,000 records and gives XGBoost
accuracy 0.9565. This completed rerun instead uses the counts above and produces
accuracy approximately 0.956938. Explain the dataset selection/run behind the
report before treating both as one consistent result. The written report has
not been amended in this package.

The source CSV contains no 2019 occurrences. The code's study window starts
on 1 January 2020. Use those dates when describing this implementation.

## Packaging verification and changes

- All original modelling source cells and every saved output are retained.
- Only the data-loading cell was adapted to locate the same CSV in Colab or the repository data directory.
- Markdown explanations and section headings were added. Colab runtime metadata was removed.
- Ten original PNG outputs were extracted, verified as readable, and included separately.
- Exact test accuracies and rounded weighted F1 values were checked against all four confusion matrices and the saved summary.
- Study-period and phase counts were independently checked against the supplied CSV.
- No model retraining was performed while preparing this package. Original environment versions were not recorded.

## References for a future revision

- Imbalanced-learn resampling and leakage guidance: https://imbalanced-learn.org/stable/common_pitfalls.html
- SMOTENC for mixed numerical/categorical features: https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTENC.html

Any changed validation design should be labelled as a revised analysis and
reported separately from the original workflow's scores.
