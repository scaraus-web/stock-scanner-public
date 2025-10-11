# Quantitative Value Strategy — Stock Selector with Backtesting (Demo)

Employer-facing demo notebook that builds a **relative-value stock table** and runs a **simple timing backtest** over a selected universe (subset of the S&P 500). The project demonstrates data handling, factor computation, and basic portfolio backtesting in a single, reviewable flow.

> **Demo / Non-Commercial.** Provided only for evaluating Serge Caraus’s work. See `LICENSE`.

---

## What this demo does

- **Universe ingestion:** reads tickers from `data/raw/sp_500_50_stocks.csv`.
- **Market data:** fetches OHLCV via Yahoo Finance (`yfinance`).
- **Value factors (lightweight fundamentals):** P/E, P/B, P/S (TTM proxies), EV/EBITDA, EV/Gross Profit (when available).
- **Technical features:** `EMA200`, `AVG_VOL` (14-day, in millions), `ATR` (14-day).
- **Performance metrics:** `Cumulative Return`, `Max Drawdown`.
- **Backtest (illustrative):** Monthly **200-DMA** timing model using `pyalgotrade`.

Outputs a single analysis table: **`Quantitative Value Stocks.csv`**.

---


---

## Quick start

### 1) Environment

**pip**
```bash
python -m venv .venv
# Windows:
. .venv/Scripts/activate
# macOS/Linux:
# source .venv/bin/activate
pip install -r requirements.txt

**conda**
conda env create -f environment.yml
conda activate value-scanner

2) Provide tickers

Create data/raw/sp_500_50_stocks.csv:

Ticker
AAPL
MSFT
NVDA
...
3) Run the notebook

Open:
notebooks/Quantitative Value Strategy Stock Selector with Backtesting code for portfolio.ipynb

Run all cells. Export a sample output:

Backtest (illustrative)

Rule: On the last NYSE trading day of each month, be long if close > 200-DMA; otherwise stay in cash.

Assumptions: No fees/slippage; full-cash allocation; demonstration only.

Limitations

Yahoo fundamentals can be sparse; EV-based ratios may be NaN.

The backtest is simplified and not investment advice.

Limitations

Yahoo fundamentals can be sparse; EV-based ratios may be NaN.

The backtest is simplified and not investment advice.

Dependencies

pandas, numpy, yfinance, pandas_market_calendars, pyalgotrade, matplotlib (if plotting). See requirements.txt.


