# Gold, the U.S. Dollar & the Gold Fear Gauge (GVZ): 2012–2025

> Is gold's record-breaking rally driven by panic or by structural demand? This project compares **Gold**, the **U.S. Dollar Index (DXY)** and the **CBOE Gold Volatility Index (GVZ)** over 14 years to find out, and turns the findings into a volatility-aware risk framework for 2026.

---

## Table of Contents

- [Overview](#overview)
- [Key Questions](#key-questions)
- [Data](#data)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [GVZ Risk-Calibration Framework](#gvz-risk-calibration-framework)
- [2026 Outlook](#2026-outlook)
- [Limitations](#limitations)
- [Repository Structure](#repository-structure)
- [Data Sources](#data-sources)
- [Disclaimer](#disclaimer)

---

## Overview

Gold has been setting new all-time highs, with prices moving past **$4,000/oz** in the latest data. Price alone cannot tell us *why* it is rising. Prices are lagging indicators, so this analysis adds a sentiment layer, the **GVZ ("fear gauge" for gold)**, to separate **panic-driven rallies** from **structurally driven rallies**.

The project:

1. Maps gold against the U.S. Dollar Index to test the classic inverse relationship.
2. Adds GVZ to measure investor anxiety during key periods.
3. Compares the 2020–2022 and 2023–2025 regimes.
4. Translates GVZ into practical **stop-loss calibration, position sizing and entry rules**.

## Key Questions

1. Does gold still move inversely to the U.S. Dollar?
2. Was the 2024–2025 rally driven by panic (high volatility) or by structural demand (low volatility)?
3. How can GVZ be used to size intraday ranges and reduce the risk of being stopped out by volatility spikes ("stop-loss hunting")?
4. What does the historical relationship imply for gold positioning in 2026?

## Data

| Item | Detail |
|---|---|
| File | `data.xlsx` (Sheet1) |
| Frequency | Monthly |
| Period | Jan 2012 – Dec 2025 (168 monthly observations) |

| Column | Description | Unit |
|---|---|---|
| `Date` | First day of each month | date |
| `Gold price` | Gold Futures price | USD |
| `Gold open price` | Gold Futures open price | USD |
| `USA dollar open price` | U.S. Dollar Index (DXY) open | index points |
| `CBOE Price` | GVZ close | % points |
| `CBOE Open` | GVZ open | % points |

> **Note:** In the workbook, the DXY and GVZ columns are `VLOOKUP` formulas that point to an external source workbook (`dollar (3)` and `CBOE Gold Volatitity Historical`). If those values appear empty or show `#REF!` when you open the file, paste them as static values or re-link the source workbook.

**What is GVZ?** The Cboe Gold ETF Volatility Index estimates the expected **30-day volatility** of returns on the SPDR Gold Shares ETF (GLD), computed from GLD option prices, the same way the VIX is built for the S&P 500. It is annualized and expressed in percentage points.

## Methodology

- **Variables:** Gold open price, DXY open price and GVZ are compared over time.
- **Regime comparison:** 2012–2018 (consolidation), 2020–2022 (pandemic and liquidity shock), 2023–2025 (structural breakout).
- **Interpretation:** Gold/DXY direction shows whether the inverse correlation holds. GVZ level and spikes show whether moves are panic-driven or calm.
- **Risk framework:** GVZ is converted to a daily expected move and then to stop distances and position sizes (see below).

## Key Findings

### 1. 2012–2018: Stability and consolidation
- DXY rose gradually from roughly 80 toward 100.
- Gold showed a clear **inverse relationship**, consolidating around **$1,200–$1,500** while the dollar strengthened.

### 2. 2020–2022: Crisis and transition
- Gold and the dollar both became highly volatile around the pandemic.
- GVZ showed **sharp, frequent spikes**, consistent with panic buying and demand for a "temporary shelter."

### 3. 2023–2025: The structural breakout
- Gold repeatedly made new all-time highs while **GVZ stayed comparatively subdued** versus the 2020 peaks.
- DXY stayed elevated (around 100), yet gold kept rising: a **decoupling** from the dollar.
- Takeaway: the 2024–2025 rally looks **qualitatively stronger** than the 2020–2022 rally. It occurred under *controlled volatility*, which points to structural drivers such as central-bank accumulation, persistent inflation and rising sovereign debt rather than short-term panic.

| Period | Gold vs. USD | GVZ behavior | Interpretation |
|---|---|---|---|
| 2012–2018 | Inverse / mirror | Not the focus | Stability, consolidation |
| 2020–2022 | Both volatile | Sharp spikes | Panic buying, crisis hedging |
| 2023–2025 | Decoupled | Relatively low | Structural, institution-driven demand |

## GVZ Risk-Calibration Framework

GVZ can be used as a **risk-calibration tool**, not just a sentiment indicator.

**1. Daily expected move** (square-root-of-time rule, ~252 trading days):

```
σ_daily (%) = GVZ / √252
σ_daily ($) = Gold Price × σ_daily (%)
```

**2. Volatility bands**
- **±1σ** covers ~68.2% of expected daily moves (normal regime).
- **±2σ** covers ~95.4% (geopolitical-noise regime). Moves into this zone often reflect liquidity sweeps rather than structural breakdowns.

**3. Volatility-adjusted stops and position sizing**

```
Stop distance  = K × σ_daily ($)          (K ≈ 1.0 – 1.5 depending on horizon)
Position size  = R / Stop distance         (R = fixed $ risk per trade)
```

Widening the stop without shrinking the position increases total risk. Sizing inversely to volatility keeps dollar risk constant.

**4. Regime table**

| GVZ | Regime | Stop / execution rule | Position size |
|---|---|---|---|
| `< 18` | Low / structural | Tight, technical swing-level stops; normal entries | 100% |
| `18 – 24` | Moderate / policy noise | Stops at ~1.25 × σ_daily; limit orders only | 70–80% |
| `> 24` | Extreme / geopolitical shock | Stops at 1.5–2.0 × σ_daily; apply the plateau rule | 40–50% |

**5. "Volatility Plateau" rule:** do not enter during a vertical GVZ spike. Wait for the rate of change in GVZ to flatten or turn negative, a sign that panic-driven sweeps have ended and price discovery has resumed.

### Signal summary

| Signal | Condition | Suggested action |
|---|---|---|
| **Accumulation** | Gold dips while GVZ stays stable or below ~15–18 | Healthy pullback: accumulate / buy the dip |
| **Conviction** | New highs while GVZ falls or stays low | Quality uptrend: hold and let profits run |
| **Defensive** | Rapid price surge with GVZ above ~25 | Avoid chasing; wait for a plateau; consider partial profit-taking |

## 2026 Outlook

Based on the 2020–2025 relationships, the analysis argues that:

- **Tariff-driven inflation** and currency-debasement concerns support gold as a hedge, as in the 2024–2025 period.
- **Monetary-policy uncertainty** (for example, political pressure on Federal Reserve rate decisions) could push GVZ higher, and historically gold has tended to attract buying when volatility rises under inflationary conditions.
- A **weekly volatility audit** is recommended: record highs with low GVZ suggest a structural bull market, while rising prices with a spiking GVZ suggest speculative excess.

> These are scenario-based interpretations of historical patterns, not forecasts or guarantees.

## Limitations

- **Monthly data vs. intraday framework.** The dataset is monthly, while the GVZ calibration framework targets intraday behavior. The thresholds (18 / 24 / 25) are illustrative heuristics and should be backtested on daily or intraday data before use.
- **Correlation is not causation.** Visual comparison of three series does not prove that central-bank buying or tariffs drove the moves. The structural-driver explanation is an interpretation.
- **Single dollar measure.** Only DXY is used. Real yields, central-bank purchases and ETF flows are not modeled.
- **Small, single-cycle sample.** One decoupling episode (2024–2025) is limited evidence that the relationship has permanently changed.
- **GVZ reflects GLD options**, not futures directly.

## Repository Structure

```
.
├── data.xlsx        # Monthly Gold, DXY and GVZ data (2012–2025)
├── README.md        # Project documentation
└── images/          # Charts used in the report (optional)
```

## Data Sources

- **Gold Futures:** [Investing.com – Gold Futures Historical Prices](https://www.investing.com/commodities/gold-historical-data)
- **U.S. Dollar Index (DXY):** [MarketWatch – DXY Price Data](https://www.marketwatch.com/investing/index/dxy)
- **GVZ:** [Investing.com – CBOE Gold Volatility Historical Data](https://www.investing.com/indices/cboe-gold-volatility-historical-data) and [Cboe Global Indices: GVZ Index Dashboard](https://www.cboe.com/us/indices/dashboard/GVZ/)
- **Reference:** Bankrate – Gold Price History and Historical Prices (1915–2025)

## Disclaimer

This project is for **educational and analytical purposes only** and is **not financial or investment advice**. Gold prices and volatility can change quickly. Do your own research or consult a licensed financial advisor before making investment decisions.
