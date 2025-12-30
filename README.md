# Trader Behavior vs Market Sentiment Analysis

## Overview
This project analyzes the relationship between **trader behavior** and **market sentiment** in the cryptocurrency market.  
Using historical trader data from Hyperliquid and the Bitcoin Fear & Greed Index, the analysis explores how profitability, risk exposure, trading volume, and directional bias vary across different market sentiment regimes.

The objective is to identify **behavioral patterns and hidden signals** that can inform smarter trading strategies.

---

## Datasets Used

### 1. Bitcoin Fear & Greed Index
- **Columns**
  - `Date`
  - `Classification`  
    (`Extreme Fear`, `Fear`, `Neutral`, `Greed`, `Extreme Greed`)
- Represents overall market sentiment on a daily basis.

### 2. Historical Trader Data (Hyperliquid)
- **Key Columns**
  - `Account`
  - `Coin`
  - `Execution Price`
  - `Size Tokens`
  - `Size USD`
  - `Side`
  - `Direction` (Long / Short)
  - `Start Position`
  - `Closed PnL`
  - `Timestamp IST`
  - `Fee`

---

## Project Structure

ds_<candidate_name>/
├── notebook_1.ipynb # Main analysis notebook (Google Colab)
├── csv_files/
│ └── merged_trader_sentiment.csv
├── outputs/
│ └── plots/
│ ├── avg_pnl_vs_sentiment.png
│ ├── win_rate_vs_sentiment.png
│ ├── trade_volume_vs_sentiment.png
│ └── exposure_vs_sentiment.png
├── ds_report.pdf # Final summarized insights
└── README.md


---

## Methodology

### 1. Data Preparation
- Converted timestamps to datetime format.
- Aligned trader data (intraday) with sentiment data (daily) using trade dates.
- Encoded market sentiment as an **ordinal sentiment score**:

| Sentiment        | Score |
|------------------|-------|
| Extreme Fear     | -2    |
| Fear             | -1    |
| Neutral          | 0     |
| Greed            | 1     |
| Extreme Greed    | 2     |

---

### 2. Feature Engineering
Since leverage data was not available, alternative **risk and behavior proxies** were constructed:

- **Trade Volume (USD)**  
  Absolute trade size in USD.
- **Profitability Flag**  
  Indicates whether a trade closed in profit.
- **Position Exposure**  
  Proxy for capital at risk using starting position and trade size.
- **Directional Bias**  
  Encoded long (+1) and short (-1) trades.

---

### 3. Analysis Focus Areas
- Profitability vs Market Sentiment
- Win Rate across Sentiment Regimes
- Trading Volume as a Measure of Risk Appetite
- Position Exposure as a Proxy for Risk
- Long vs Short Bias under Different Market Conditions

---

## Key Insights (Summary)

- Trading volume and exposure increase significantly during **Greed** and **Extreme Greed** phases.
- Profitability does not scale proportionally with increased risk-taking.
- Losses tend to be amplified during **Extreme Fear** regimes.
- Win rates remain relatively stable, suggesting increased risk rather than improved strategy during optimistic market conditions.

Detailed interpretations are available in `ds_report.pdf`.

---

## Tools & Technologies
- Python (Pandas, NumPy)
- Matplotlib & Seaborn for visualization
- Google Colab for analysis
- GitHub for version control and submission

---

## Notes
- All analysis was performed in Google Colab.
- Notebook links are shared with **view-only access**.
- Folder structure strictly follows the assignment submission guidelines.

---

## Author
<Roshan Laharwani>
Data Science Assignment – Web3 Trading Team
