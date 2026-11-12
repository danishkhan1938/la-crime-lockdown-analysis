# Data setup

Provider: City of Los Angeles / LAPD.

Official catalogue: https://catalog.data.gov/dataset/crime-data-from-2020-to-present

The source has historically been called **Crime Data from 2020 to Present**, and the catalogue now labels it **Crime Data from 2020 to 2024**.

For the supplied snapshot, extract `Crime_Data_from_2020_to_Present.csv` from your original artifact ZIP and place it in this directory. The CSV is intentionally excluded from the repository package.

The attached CSV has 910,707 data rows and 232,591,157 bytes. Occurrence years: 2020 (199,617), 2021 (209,596), 2022 (234,784), 2023 (230,610), and 2024 (36,100). These counts were inspected directly, not inferred from the report.

The notebook applies its own date filter after loading. A fresh download may differ from the submitted snapshot. Record source, download date, file hash and filtering steps for any new run. The original snapshot date and the selection behind the saved 40,875-row run remain unconfirmed. Do not assume the current download reproduces those results.
