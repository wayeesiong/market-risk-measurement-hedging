# Market Risk Measurement and Hedging Strategy Analysis

### A $1 Billion Hong Kong Equity Index Portfolio

Excel-based market risk analysis evaluating portfolio exposure, tail risk and derivative hedging strategies across a diversified Hong Kong / China equity index portfolio.

---

## Project Overview

This academic group project evaluates the market risk of a hypothetical **$1 billion equity portfolio** invested equally across five Hong Kong and China-related stock indices.

The analysis combines portfolio construction, market beta estimation, Value at Risk (VaR), Expected Shortfall (ES), Monte Carlo simulation and derivative hedging to assess both the magnitude of potential losses and alternative approaches to managing market exposure.

The portfolio consists of:

- Hang Seng Index (HSI)
- FTSE China 50 Index
- Hang Seng TECH Index (HSTECH)
- Hang Seng China Enterprises Index (HSCEI)
- Hang Seng China-Affiliated Corporations Index (HSCCI)

Each index represents **20% of the initial $1 billion portfolio**.

---

## Objectives

The project addresses four main questions:

1. How much market risk is embedded in the portfolio?
2. How sensitive is the portfolio to movements in the S&P 500?
3. How do different VaR methodologies estimate potential losses?
4. How effectively can futures and options be used to hedge market exposure?

---

## Data

The analysis uses historical market data covering the five portfolio indices together with:

- S&P 500 Index
- USD/HKD exchange rate

Index values are converted into U.S. dollar terms before portfolio returns and risk measures are calculated.

The final dataset contains **316 portfolio observations**.

---

## Methodology

### 1. Portfolio Construction

A hypothetical **$1 billion portfolio** is allocated equally across the five selected equity indices:

| Index | Portfolio Weight |
|---|---:|
| Hang Seng Index | 20% |
| FTSE China 50 | 20% |
| Hang Seng TECH Index | 20% |
| Hang Seng China Enterprises Index | 20% |
| Hang Seng China-Affiliated Corporations Index | 20% |

---

### 2. Market Beta Analysis

Portfolio returns are regressed against S&P 500 returns to estimate systematic market exposure.

The estimated portfolio beta is approximately:

**β = 0.2554**

This suggests that the portfolio has relatively low sensitivity to movements in the U.S. equity market.

However, the regression produces an R² of approximately **1.31%**, indicating that S&P 500 returns explain only a small portion of the portfolio's daily return variation.

---

### 3. Historical Simulation VaR

Historical portfolio returns are used directly to estimate losses without imposing a normal distribution assumption.

At the **99% confidence level**:

- VaR ≈ **$39.88 million**
- Expected Shortfall ≈ **$85.97 million**

The large difference between VaR and Expected Shortfall reflects the presence of extreme historical losses.

---

### 4. Delta-Normal VaR

A parametric VaR approach is applied using the portfolio mean and standard deviation under a normal-distribution assumption.

At the **99% confidence level**:

- VaR ≈ **$41.37 million**
- Expected Shortfall ≈ **$47.61 million**

---

### 5. Monte Carlo Simulation

Monte Carlo simulation is used to generate potential portfolio-loss scenarios.

Using **1,000 simulations**:

- VaR ≈ **$39.93 million**
- Expected Shortfall ≈ **$45.74 million**

---

## VaR Comparison

| Method | 99% VaR | 99% Expected Shortfall |
|---|---:|---:|
| Historical Simulation | $39.88m | $85.97m |
| Delta-Normal | $41.37m | $47.61m |
| Monte Carlo | $39.93m | $45.74m |

Although the three methods generate relatively similar VaR estimates, their Expected Shortfall estimates differ substantially.

This highlights how model assumptions can materially affect the measurement of extreme tail losses.

---

## Portfolio Risk Characteristics

The portfolio return/value distribution exhibits:

- Negative skewness
- High kurtosis
- Fat-tail characteristics

Portfolio-value kurtosis is approximately **10.88**, suggesting that extreme outcomes occur more frequently than would be expected under a normal distribution.

This is particularly important when interpreting parametric risk models.

---

## Hedging Strategies

Three approaches are compared:

### Strategy 1 — Unhedged Portfolio

The portfolio remains fully exposed to market movements.

Because the portfolio beta is relatively low, its sensitivity to S&P 500 movements is limited, but substantial downside exposure remains during severe market declines.

---

### Strategy 2 — E-mini S&P 500 Futures Hedge

A short position in E-mini S&P 500 futures is constructed using the estimated portfolio beta.

The futures hedge substantially offsets changes in portfolio value caused by movements in the S&P 500.

Under the scenario analysis, the hedged portfolio remains close to its initial **$1 billion value** across both rising and falling market scenarios.

The trade-off is that protection from downside risk also removes most of the potential upside associated with market movements.

---

### Strategy 3 — E-mini S&P 500 Put Options

Put options are used to create downside protection while preserving upside participation.

The strategy assumes a September-expiry E-mini S&P 500 put option with:

- Strike price: **5,550**
- Option price: **$40.75**
- Contract multiplier: **$50**
- Total premium: approximately **$1.87 million**

Unlike the futures hedge, the option strategy allows the portfolio to continue benefiting from favourable market movements while establishing downside protection.

---

## Hedging Comparison

| Strategy | Downside Protection | Upside Participation | Main Cost |
|---|---|---|---|
| Unhedged | Low | Full | Market exposure |
| Futures Hedge | High | Very limited | Opportunity cost / implementation |
| Put Option Hedge | High | Retained | Option premium |

The appropriate hedging strategy therefore depends on the portfolio manager's market outlook, risk tolerance and willingness to incur hedging costs.

---

## Key Findings

- The portfolio exhibits relatively low S&P 500 sensitivity with a beta of approximately **0.2554**.
- The low regression R² indicates that U.S. market movements explain only a small proportion of total portfolio risk.
- 99% VaR estimates are relatively stable across the three methodologies at approximately **$40–41 million**.
- Expected Shortfall varies much more substantially across methodologies.
- Historical simulation captures severe observed tail events that are not reflected as strongly in the parametric and simulated approaches.
- Futures hedging provides strong market-neutralisation but removes most upside exposure.
- Put options provide asymmetric protection by limiting downside while maintaining participation in favourable markets.

---

## Risk Management Considerations

The project also considers broader implementation issues including:

- Hedging costs
- Margin and collateral requirements
- Liquidity
- Strategy complexity
- Regulatory compliance
- Cross-department risk coordination
- Risk appetite
- Firmwide risk aggregation

These factors demonstrate that effective risk management extends beyond quantitative risk measurement alone.

---

## Limitations

Several limitations should be considered when interpreting the results:

- The portfolio uses historical market relationships that may change over time.
- The S&P 500 regression has low explanatory power, creating potential basis risk when S&P 500 derivatives are used to hedge a Hong Kong / China-focused portfolio.
- Historical Simulation results depend on the selected observation window.
- Delta-Normal VaR relies on a normal-distribution assumption despite the portfolio exhibiting negative skewness and high kurtosis.
- Monte Carlo estimates are affected by simulation assumptions and the number of replications.
- Hedge effectiveness depends on the stability of beta and cross-market correlations.
- Real-world transaction costs, liquidity constraints, margin requirements and implementation frictions may affect hedging outcomes.

---

## Repository Structure

```text
market-risk-measurement-hedging/
│
├── README.md
│
├── data/
│   ├── README.md
│   └── market-risk-dataset.xlsx
│
├── analysis/
│   ├── README.md
│   └── market-risk-analysis.xlsm
│
└── report/
    ├── README.md
    └── market-risk-measurement-hedging-analysis.pdf
