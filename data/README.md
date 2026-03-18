# Data

This directory holds the extended CPZ cross-sectional equity dataset.
The files are **not stored in this repository** (they are excluded by
`.gitignore`) because they contain commercially licensed data from
CRSP and Compustat that cannot be redistributed publicly.

## Generating the Data

The dataset is produced by the companion repository:

**[cpz-equity-data-pipeline](https://github.com/amos-anderson/cpz-equity-data-pipeline)**

Follow the README there to run the full pipeline. You will need:
- A WRDS account with access to CRSP, Compustat, and Fama-French data
- Approximately 2.5 GB of free disk space
- 2–3 hours of compute time

## Expected File Locations

After running the pipeline, place the output files here:
```
data/
└── extended_v2/
    ├── train.parquet    # 1967–1989, 489,885 rows
    ├── valid.parquet    # 1990–1999, 376,018 rows
    └── test.parquet     # 2000–2024, 739,286 rows
```

## Dataset Summary

| Split | Period | Rows | Avg Stocks/Month |
|-------|--------|------|-----------------|
| Train | 1967–1989 | 489,885 | 1,775 |
| Valid | 1990–1999 | 376,018 | 3,133 |
| Test  | 2000–2024 | 739,286 | 2,464 |
| **Total** | **1967–2024** | **1,605,189** | **2,300** |

## Key Columns

| Column | Description |
|--------|-------------|
| `permno` | CRSP permanent security identifier |
| `date` | Month-end date |
| `ret_excess` | Monthly excess return (return − risk-free rate) |
| `me` | Market equity in $millions |
| 46 characteristics | Rank-normalized to (−0.5, 0.5) within each month |