# Pair Trading Strategy: BNP Paribas - L'Oréal

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Complete-success)

Implementation of a **pair trading** (statistical arbitrage) strategy on two CAC40 stocks, with rigorous backtesting and comprehensive performance analysis.

---

## Project Objective

Develop a market-neutral quantitative strategy based on **cointegration** between BNP Paribas and L'Oréal, capable of generating positive returns regardless of market direction.

**Result achieved**: +11.26% annualized return with a Sharpe Ratio of 0.58 over the 2019-2024 period.

---

## Key Results

| Metric | Value |
|--------|-------|
| **Total Return** | +67.84% |
| **Annualized Return** | +11.26% |
| **Sharpe Ratio** | 0.58 |
| **Sortino Ratio** | 0.50 |
| **Maximum Drawdown** | -38.12% |
| **Win Rate** | 56.21% |
| **Number of Trades** | 25 (over 5 years) |

---

## Methodology

### 1. Pair Selection
- Correlation analysis on 5 CAC40 stocks
- **Engle-Granger cointegration test**
- Selection of BNP.PA - OR.PA (p-value = 0.0234 < 0.05 ✓)

### 2. Spread Modeling
- Linear regression to calculate the **hedge ratio** (β = 6.56)
- Spread construction: `Spread = OR.PA - 6.56 × BNP.PA`
- Stationarity verification

### 3. Signal Generation
- **Z-score** calculation on 60-day rolling window
- **Long spread** if z-score < -2.0
- **Short spread** if z-score > +2.0
- **Exit** if |z-score| < 0.5

### 4. Backtesting
- Period: 2019-2024 (1283 trading days)
- Returns calculation weighted by hedge ratio
- Metrics: Sharpe, Sortino, Calmar, Max Drawdown

---

## Technologies Used

- **Python 3.8+**
- `yfinance` - Financial data download
- `pandas` & `numpy` - Data manipulation
- `statsmodels` - Cointegration tests
- `scikit-learn` - Linear regression
- `matplotlib` & `seaborn` - Visualizations

---

## Project Structure
```
pair-trading-bnp-loreal/
│
├── notebook/
│   └── pair_trading_analysis.ipynb    # Complete Jupyter notebook
│
├── requirements.txt                    # Python dependencies                         
└── README.md                             
```

---

## Installation and Usage

### Prerequisites
```bash
Python 3.8 or higher
pip
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/[your-username]/pair-trading-bnp-loreal.git
cd pair-trading-bnp-loreal
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Launch the notebook**
```bash
jupyter notebook notebook/pair_trading_analysis.ipynb
```

---

## Dependencies
```txt
yfinance>=0.2.28
pandas>=1.5.0
numpy>=1.23.0
matplotlib>=3.6.0
seaborn>=0.12.0
statsmodels>=0.14.0
scikit-learn>=1.2.0
jupyter>=1.0.0
```

---

## Strengths

- **Statistically validated cointegration** (p-value = 0.0234)
- **Market-neutral strategy** (low sensitivity to general market movements)
- **Selective approach** (25 trades over 5 years, no overtrading)
- **Positive performance** (+11.26% annualized)
- **Win rate above 50%** (56.21%)

---

## Identified Limitations

- **High drawdown in 2020** (-38% during COVID-19)
- **Modest Sharpe Ratio** (0.58, target: > 1.0)
- **Transaction costs not included** (estimated impact: -5 to -10%)
- **Non-optimized parameters** (arbitrary window and thresholds)
- **No walk-forward analysis** (overfitting risk)

---

## Key Concepts

| Concept | Explanation |
|---------|-------------|
| **Cointegration** | Long-term equilibrium relationship between two time series |
| **Hedge Ratio** | Coefficient determining the relative weights of the two positions |
| **Z-score** | Normalized deviation measure of the spread from its mean |
| **Mean Reversion** | Tendency of a series to return to its mean |
| **Market-Neutral** | Strategy with low sensitivity to general market movements |

---

## Resources and References

- **Engle-Granger (1987)** - Co-Integration and Error Correction
- **Alexander, C. (1999)** - Optimal Hedging Using Cointegration
- **Vidyamurthy, G. (2004)** - Pairs Trading: Quantitative Methods and Analysis
- [Statsmodels Documentation](https://www.statsmodels.org/)
- [Quantitative Finance on StackExchange](https://quant.stackexchange.com/)

---
