# COVID-19 Lockdowns and Urban Crime in Los Angeles

**Danish Ahsan Khan | MSc Data Analytics, Dublin Business School**

A dissertation project exploring temporal crime patterns and classifying recorded incidents as violent or non-violent using Python and machine learning.

**Status: repository preparation draft.** The supplied report, saved notebook outputs, and CSV represent inconsistent record counts and results. This is an archive of the analysis workflow, not a verified reproduction. See [review notes](docs/REVIEW_NOTES.md).

## Research focus

- Explore recorded crime counts across the study's defined pandemic phases.
- Compare Logistic Regression, Random Forest, SVM, and XGBoost for incident classification.
- Evaluate accuracy, precision, recall, weighted F1, and confusion matrices.

## Implementation

The notebook filters incident dates from 1 January 2020 through 19 June 2023. It derives temporal and victim-age features and assigns a binary label using a manually specified offence-description list. It uses a stratified 70/30 train/test split, samples up to 10,000 training records, applies imputation, ordinal encoding and SMOTE, and tunes models using five-fold cross-validation.

The implementation uses incident attributes such as weapon description. It classifies existing records; it does not establish an ability to forecast future crimes. Descriptive changes do not establish that lockdowns caused those changes.

## Files

| Path | Contents |
|---|---|
| `notebooks/crime_analysis.ipynb` | Original analysis logic with a portable data path and cleared outputs |
| `data/README.md` | Source and local data setup |
| `results/saved_run_metrics.csv` | Metrics transcribed from the supplied notebook, not rerun |
| `docs/REVIEW_NOTES.md` | Reproducibility discrepancies and methodological limitations |
| `docs/UPLOAD_GUIDE.md` | Steps for uploading this folder to GitHub |
| `requirements.txt` | Imported dependencies, with versions not recovered |

## Run locally

Use a Python environment with compatible versions of the packages below. The original environment was not supplied; this dependency list is not a tested lockfile.

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
cd notebooks
jupyter lab
```

Place the CSV as described in [data setup](data/README.md), open `crime_analysis.ipynb`, and run cells from top to bottom. The full CSV makes the test set much larger than in the saved run; SVM evaluation and grid searches may be slow. Record the exact data snapshot and installed package versions when rerunning.

## Historical results, pending reconciliation

| Model | Saved test accuracy | Saved weighted F1 |
|---|---:|---:|
| Logistic Regression | 0.933540 | 0.933352 |
| Random Forest | 0.947484 | 0.948116 |
| SVM | 0.934437 | 0.934270 |
| XGBoost | 0.947566 | 0.948146 |

These are existing notebook outputs, not independently validated results. Do not substitute the different report metrics without identifying the corresponding run. The saved XGBoost and Random Forest scores are nearly identical; no significance test establishes superiority.

## Limitations and next steps

Reconcile the dataset and report, place preprocessing and any resampling inside cross-validation folds, review categorical resampling, and rerun before presenting performance as final. Compare phase-normalised rates rather than unequal-duration totals. See the review notes for details.

The dissertation report and presentation are not included in this code package. Add reviewed public copies separately after removing personal identifiers and resolving inconsistent findings. No licence has been selected for the author's code; data remains subject to its provider's terms.
