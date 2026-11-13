# Results provenance

These files describe the completed original-workflow Colab rerun supplied by
the author on 13 November 2026. They replace the earlier draft's saved scores.
All four models use the same 225,281-record test partition. Model fitting uses
a 10,000-record sample from the separate training partition; SMOTE expands it
to 14,376 training rows.

- `saved_run_metrics.csv`: test accuracy and weighted F1 checked against the notebook summary and confusion matrices. Decimal values have not been converted to percentages.
- `model_details.json`: confusion matrices (rows true, columns predicted), precision/recall, macro F1, best parameters, and original cross-validation scores.
- `phase_summary.csv`: original phase counts divided by inclusive calendar-day exposure. Daily averages are supplementary calculations and do not change the notebook's model results.
- `run_summary.json`: input hashes, class counts, split sizes and limitations.

Original CV scores were obtained after preprocessing and SMOTE on the training
sample, before cross-validation. They must not be treated as results from the
optional revised pipeline. The test partition is separate and not resampled.

No models were retrained during packaging. The notebook's exact floating-point
accuracy values and six-decimal summary were checked against the recorded
confusion matrices. Environment versions were not recorded, so exact bitwise
reproduction is not guaranteed.
