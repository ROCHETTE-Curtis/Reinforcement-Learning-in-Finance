# Physics-Inspired Models for Financial Time Series

Two complementary approaches to modeling stock returns using stochastic dynamics: linear mean reversion (IRL) and non-linear potential wells (QED).

## Models

### Inverse Reinforcement Learning (IRL)
Linear mean-reversion dynamics with adaptive equilibrium:
```
dX = (weighted_signals + κ(θ_t - X)) dt + σ dW
```
- θ moves with cumulative signal returns
- Direct MLE estimation in log-space
- Fast calibration, interpretable parameters

### Quantum Equilibrium-Disequilibrium (QED)
Non-linear dynamics with metastable potential wells:
```
dy = (θ - 0.5σ² + signals - κe^y - ge^(2y)) dt + σ dW
```
- Quartic potential creates double-well structure
- Kramers escape rate quantifies regime stability
- Barrier-based position sizing

## Signal Stack (Both Models)
- **MA10/MA30:** Rolling mean returns (10/30 day windows)
- **VAM:** Volatility-adjusted momentum with adaptive lookback (10-60 days)

## Results

**IRL (S&P sample, OOS):**
- 4.5% RMSE improvement over random walk
- VAM added 0.7% incremental improvement

**QED (DJI-30, OOS 2016-2017):**
- 11.5% annual return vs 8.2% benchmark
- Sharpe 2.19 vs 0.72
- Max drawdown -4.7% vs -13.2%
- Note: 40% daily turnover; transaction costs material

## Key Difference

**IRL** models prices as reverting to a moving target that tracks signal momentum—suitable for trend-following with mean-reversion overlay.

**QED** models prices as trapped in potential wells that can break down—suitable for regime-dependent strategies where barrier strength determines position size.

## Structure
```
├── data/
│   ├── dja_cap.csv           # Dow Jones 30 (2010-2017)
│   └── spx_holdings.csv      # S&P sample (2010-2023)
├── notebooks/
│   ├── irl_model.ipynb       # IRL calibration
│   └── qed_model.ipynb       # QED + backtests
└── README.md
```

## Dependencies
```
tensorflow>=2.10
numpy>=1.21
pandas>=1.3
matplotlib>=3.4
```

## Usage

Both models follow similar workflow:
1. Signal generation (MA + VAM)
2. MLE parameter estimation
3. Model validation

QED adds barrier analysis and continuous position scaling for trading.

## Limitations

- Single-period backtests (no walk-forward robustness testing)
- Transaction costs not modeled in IRL
- QED shows numerical instabilities at extreme barrier strengths
- Limited to technical signals (no fundamental data)

## References

- Halperin & Feldshteyn: "Market Self-Learning of Signals" (IRL framework)
- Kramers: "Brownian Motion in Field of Force" (Escape rate theory)
- Black & Litterman: "Global Portfolio Optimization" (IRL connection)
