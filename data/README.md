# Dataset source and setup

Provider: City of Los Angeles / Los Angeles Police Department (LAPD).

Official catalogue: https://catalog.data.gov/dataset/crime-data-from-2020-to-present

Dataset identifier: `2nrs-mtv8`. This source was historically called **Crime Data
from 2020 to Present**; the catalogue now uses **Crime Data from 2020 to 2024**.

For the exact supplied snapshot, extract `Crime_Data_from_2020_to_Present.csv`
from your original dissertation artifact ZIP. Place the CSV in this `data/`
directory for local use, or upload it into Colab's Files panel. The notebook
detects either location. A fresh provider download may contain different rows.

| Snapshot property | Value |
|---|---|
| Raw records | 910,707 |
| Columns | 28 |
| File bytes | 232591157 |
| Study window | 2020-01-01 to 2023-06-19, inclusive |
| Study records | 750,936 |
| SHA-256 | `051b14448401f8433e6478aafba4ef190fdbcc073e505a9c60a9ac834c05d78a` |

The source snapshot's original download date was not recorded. The CSV includes
2020–2024 occurrences; the notebook filters the study window. It contains no
2019 data, so this implementation should not be described as a 2019–2023 study.

Keep the large CSV outside GitHub and refer readers to the provider. Review
the provider's terms for any redistribution. Hash and record the date of any
new download so differences between runs can be understood.
