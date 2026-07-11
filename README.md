# oil-factor-signal-research

Oil Factor Signal Research

Research into whether a proprietary factor ("Factor A") carries predictive
information about crude oil returns, and how best to convert it into a
long / short / neutral trading signal.

Objective

Given a daily factor series and daily oil prices over roughly ten years
(July 2016 to July 2026), the goal is to identify the best way to use the
factor to trade oil, and to judge honestly whether the signal is real or
whether it is an artefact of overfitting.

Data

data/20260705_oil_price_factor.xlsx — 2,521 daily observations.

ColumnDescriptionDateTrading datefactor AProprietary factor level (cumulative, index-like, ~100 in 2016 rising to ~820 in 2026)daily returnDaily return of Factor Aoil priceCrude oil pricedaily return.1Daily return of the oil price

Notes on the data: the file is ordered newest-first, so it is sorted
ascending before analysis. Factor A is a growing, non-stationary level
series, so signals are built on rolling, standardised transformations of
the factor rather than on its raw level.

Approach


Predictive power. Measure the factor's information coefficient (IC)
against forward oil returns at 1, 5 and 20 day horizons, with
significance testing, to establish whether the factor predicts oil
returns at all and at which horizon it is strongest.
Signal construction. Convert the factor into long / short / neutral
positions using rolling standardisation (z-score) and rolling quantile
rules, so the signal adapts to changing factor levels over time.
Validation. Split the sample into training, validation and a fully
held-out test period. Approaches are compared on the validation set;
the final choice is evaluated once on the untouched test set to avoid
overfitting.
Evaluation. Strategies are judged on out-of-sample annualised Sharpe
ratio, maximum drawdown and consistency between in-sample and
out-of-sample performance, with transaction costs included. Hit rate is
reported for context only.
Regime analysis. Performance is broken down by volatility regime to
test whether the signal is robust across market conditions or dependent
on a single environment.


Repository structure

oil-factor-signal-research/
├── data/
│   └── 20260705_oil_price_factor.xlsx
├── notebooks/
│   └── oil_factor_signal_research.ipynb
├── README.md
└── requirements.txt
