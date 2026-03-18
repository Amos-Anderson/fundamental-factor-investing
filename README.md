# Fundamental Factor Investing: A Cross-Sectional Equity Research Pipeline

A rigorous, end-to-end implementation of classical cross-sectional factor
investing, built on the theoretical foundations of the Stochastic Discount
Framework and the Fama-MacBeth (1973) methodology.

This project extends the dataset of Chen, Pelger & Zhu (2020) through
December 2024 and implements a complete research pipeline — from raw
characteristic construction through live paper trading — using 46 firm
characteristics across all US common stocks.

---

## Project Architecture

### Theoretical Foundation (M0)

The theoretical backbone of the project is documented in the written report
(`report/`). It covers:

- The Stochastic Discount Factor (SDF) framework: asset pricing in
  the absence of arbitrage, the Hansen-Jagannathan bound, and the
  connection between SDFs and factor models
- The Fama-MacBeth (1973) two-pass estimator: derivation, properties,
  and the Shanken (1992) errors-in-variables correction
- The risk vs. mispricing debate: rational vs. behavioral explanations
  for characteristic-based return predictability
- The factor zoo: multiple testing, the Harvey-Liu-Zhu (2016) critique,
  and the BH-FDR correction

### Module Roadmap

| Module | Title | Status |
|--------|-------|--------|
| M0 | Theoretical Foundations | In Report |
| M1 | Factor Construction | 🔲 Pending |
| M2 | Fama-MacBeth Regression | 🔲 Pending |
| M3 | Factor Orthogonalization | 🔲 Pending |
| M4 | Signal Evaluation | 🔲 Pending |
| M5 | Portfolio Construction | 🔲 Pending |
| M6 | Walk-Forward Backtesting | 🔲 Pending |
| M7 | Paper Trading | 🔲 Pending |

---

## Module Descriptions

### M1 - Factor Construction
Constructs long-short factor portfolios from the 46 firm characteristics.
Derives value factors from the Gordon Growth Model, profitability factors
from the Modigliani-Miller framework, and investment factors from q-theory.
Implements cross-sectional ranking and factor portfolio formation.

**Key outputs:** Monthly factor return series, factor exposure matrices,
characteristic summary statistics.

### M2 - Fama-MacBeth Regression
Implements the two-pass Fama-MacBeth estimator. First pass: time-series
regressions of returns on characteristics to estimate factor loadings.
Second pass: monthly cross-sectional regressions of returns on loadings
to estimate risk prices. Applies Newey-West HAC standard errors and the
Shanken (1992) errors-in-variables correction.

**Key outputs:** Risk price estimates, t-statistics, R² decomposition,
Shanken-corrected confidence intervals.

### M3 - Factor Orthogonalization
Applies the residual maker $M = I - X(X'X)^{-1}X'$ to separate the
independent contribution of each characteristic from shared information.
Identifies which factors retain pricing power after controlling for all
others.

**Key outputs:** Orthogonalized factor returns, partial R² decomposition,
redundancy analysis.

### M4 - Signal Evaluation
Evaluates the predictive quality of each characteristic using information
coefficients (IC), IC information ratio (ICIR), factor decay curves, and
the Benjamini-Hochberg False Discovery Rate (BH-FDR) correction for
multiple testing.

**Key outputs:** IC/ICIR ranking table, decay curves, BH-adjusted
significance thresholds, signal stability analysis.

### M5 - Portfolio Construction
Constructs long-short factor portfolios using quadratic programming with
KKT conditions. Incorporates transaction cost models and turnover
constraints. Implements both equal-weighted and optimized weighting schemes.

**Key outputs:** Optimized portfolio weights, turnover statistics,
net-of-cost return series.

### M6 - Walk-Forward Backtesting
Evaluates strategy performance using a walk-forward framework with
purge and embargo periods to prevent look-ahead bias. Reports Sharpe
ratio, Information Ratio, Maximum Drawdown, and Calmar ratio.

**Key outputs:** Full equity curve, rolling performance statistics,
drawdown analysis, regime performance breakdown.

### M7 - Paper Trading
Live implementation on a Charles Schwab paper trading account.
Tracks real-time signal generation, order execution, and portfolio
management against the backtested strategy.

**Key outputs:** Live trade log, performance vs. backtest comparison,
implementation shortfall analysis.

---

## Data

This project uses a custom-constructed dataset that replicates and extends
the CPZ (2020) cross-sectional equity dataset from 1967–2016 to 1967–2024.

The data pipeline is maintained as a separate repository:
[cpz-equity-data-pipeline](https://github.com/amos-anderson/cpz-equity-data-pipeline)

The dataset contains:
- 1,605,189 stock-month observations
- 12,444 unique firms
- 46 rank-normalized firm characteristics
- Monthly excess returns (return − risk-free rate)
- Coverage: January 1967 – December 2024

**Data is not stored in this repository.** See `data/README.md` for
instructions on generating the dataset from WRDS.

---

## Setup and Installation

### Requirements
- Python 3.11+
- Conda (recommended)
- WRDS account (for data generation only)

### Installation
```bash
git clone https://github.com/amos-anderson/fundamental-factor-investing.git
cd fundamental-factor-investing
conda env create -f environment.yml
conda activate factor-investing
jupyter lab
```

### Data Setup

Follow the instructions in `data/README.md` or generate the dataset
directly from the companion repository:
[cpz-equity-data-pipeline](https://github.com/amos-anderson/cpz-equity-data-pipeline)

Once generated, place the parquet files at:
```
data/extended_v2/train.parquet
data/extended_v2/valid.parquet
data/extended_v2/test.parquet
```

---

## Theoretical References

| Topic | Key Reference |
|-------|---------------|
| SDF Framework | Cochrane (2001), *Asset Pricing* |
| Fama-MacBeth Estimator | Fama & MacBeth (1973) |
| EIV Correction | Shanken (1992) |
| Cross-Sectional Returns | Fama & French (1992, 1993) |
| Factor Zoo | Harvey, Liu & Zhu (2016) |
| Deep Learning in AP | Chen, Pelger & Zhu (2024) |
| Characteristic Selection | Freyberger, Neuhierl & Weber (2020) |
| Gross Profitability | Novy-Marx (2013) |
| Momentum | Jegadeesh & Titman (1993) |
| Multiple Testing | Benjamini & Hochberg (1995) |

---

## License

MIT License. See `LICENSE` for details.

---

## Author

Amos Anderson
MS Quantitative Finance
Stony Brook University, Spring 2026