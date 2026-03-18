# M2 — Factor Construction

## Status
🔲 Not started

## Objective
Construct long-short factor portfolios from the 46 firm characteristics
in the CPZ extended dataset. Derive value factors from the Gordon Growth
Model, profitability factors from Modigliani-Miller, and investment
factors from q-theory. Implement cross-sectional ranking and factor
portfolio formation.

## Key Inputs
- `data/extended_v2/train.parquet`
- `data/extended_v2/valid.parquet`
- `data/extended_v2/test.parquet`

## Key Outputs
- Monthly factor return series (long-short decile spreads)
- Factor exposure matrices
- Characteristic summary statistics

## Notebook
`M1_Factor_Construction.ipynb`

## Theoretical Background
See `report/` - Section on Factor Construction,
Gordon Growth Model, Modigliani-Miller, q-theory.