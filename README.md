# 📈 Portfolio Optimiser — Efficient Frontier & Sharpe Ratio

Markowitz **mean-variance optimisation** on a multi-asset (ASX + global) universe — the foundation of quantitative asset allocation used by asset managers and quant teams. The notebook maps the feasible risk-return space, solves for the **max-Sharpe (tangency)** and **minimum-variance** portfolios, and traces the full **efficient frontier**.

## What it does
<img width="1353" height="779" alt="image" src="https://github.com/user-attachments/assets/9a4b7eee-70d8-4f0b-a210-f0c550a59c52" />


| Step | Method |
|------|--------|
| **Data** | 5 years of daily prices for 6 assets via `yfinance` (auto-adjusted) |
| **Inputs** | Annualised expected returns (log) and covariance matrix |
| **Simulation** | 20,000 random long-only portfolios to visualise the risk-return cloud |
| **Optimisation** | `scipy` SLSQP — max-Sharpe (tangency) and minimum-variance, fully-invested, long-only |
| **Efficient frontier** | Minimum-variance portfolio across a grid of 50 target returns |
| **Visualisation** | Frontier, Capital Market Line, optimal portfolios, allocation comparison |

## Universe

- **Equities:** ASX 200 (STW.AX), S&P 500 (SPY), International Developed (EFA), Emerging Markets (EEM)
- **Fixed income:** US Long Treasury (TLT)
- **Commodities:** Gold (GLD)

## Method

- Portfolio return: **R_p = wᵀμ**
- Portfolio volatility: **σ_p = √(wᵀΣw)**
- Sharpe ratio: **(R_p − R_f) / σ_p**, R_f = RBA cash rate (~4%)

Constraints: weights sum to 1 (fully invested); 0 ≤ wᵢ ≤ 1 (long-only).

## Key outputs

- Efficient frontier over a random-portfolio cloud coloured by Sharpe ratio
- Max-Sharpe (tangency) and minimum-variance optimal weights
- Capital Market Line through the tangency portfolio
- Allocation comparison: Max-Sharpe vs Min-Variance vs Equal-Weight

## Setup

```bash
pip install -r requirements.txt
jupyter notebook portfolio_optimiser.ipynb
```

## Tech stack

Python · NumPy · Pandas · SciPy (SLSQP) · yfinance · Matplotlib

## Author

**Athulya Krishna Sabu** — Master of International Economics & Finance, University of Queensland
