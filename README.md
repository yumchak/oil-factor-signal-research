# Oil Factor Signal Research

Analysis of whether a proprietary factor ("Factor A") predicts crude oil returns,
and how best to trade it with long / short / neutral positions.

## Finding

The factor carries genuine but **decaying** predictive information.

| Period | Sharpe | Oil (passive) |
|---|---|---|
| Train 2016–20 | 1.36 | 0.28 |
| Validation 2021–23 | 0.23 | 0.53 |
| **Test 2024–26** (untouched) | **0.32** | 0.16 |

Strong through 2020, deteriorated sharply in early 2021, now a weak residual.
**Not deployable standalone** — but uncorrelated with oil (ρ = −0.04), so it may
have value as one component of a multi-signal book.

## Strategy

- **Signal:** factor's 5-day momentum, standardised by a 60-day rolling z-score
- **Positions:** long if z > +0.25, short if z < −0.25, otherwise flat
- **Sizing:** scaled to a 10% annualised volatility target
- **Costs:** 5 bps per unit traded, ~25× annual turnover

## Method

Rank IC screening at 1/5/20-day horizons established that the factor's *momentum*
predicts oil (IC +0.065, p = 0.001) while its *level* does not — the level's apparent
signal was directional bias, not forecasting content.

Parameters were selected on a validation set and the test period evaluated once.
The threshold was chosen for **stability** rather than peak performance; the rejected
peak subsequently returned −0.09 out of sample while the stable choice held at +0.32.
