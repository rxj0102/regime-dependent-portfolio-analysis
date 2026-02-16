# regime-dependent-portfolio-analysis
A production-ready framework for regime-dependent portfolio analysis using Python, including VIX-based regime detection, ML predictions, and risk management across 13 multi-asset classes (2015–2026 data)


# 📈 Regime-Dependent Portfolio Analysis

[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter Notebook](https://img.shields.io/badge/Made%20with-Jupyter-orange)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Project Overview

This repository contains a comprehensive, end-to-end portfolio analysis framework designed for a multi-asset portfolio. The core thesis is that **markets are not static**—they transition through different regimes (Quiet, Normal, Turbulent) based on volatility (VIX). This project explores how these regimes impact asset returns, correlations, and risk, and concludes by building and backtesting a practical regime-switching investment strategy.

Unlike standard portfolio optimization projects that assume a static market, this analysis demonstrates a sophisticated understanding of dynamic market conditions and their implications for portfolio construction and risk management.

---

## ✨ Key Features & Analysis

This notebook implements a complete quantitative workflow:

1.  **Data Acquisition & Preparation**
    *   Downloads historical data (2015-2026) for a realistic multi-asset portfolio: **Equities (SPY, QQQ, EEM, IWM, EFA), Fixed Income (TLT, HYG, LQD, SHY), and Alternatives (GLD, USO, VNQ, DBC)**.
    *   Cleans and structures data for analysis.

2.  **Market Regime Classification**
    *   Defines market states using the VIX index: **Quiet (VIX < 15), Normal (15 ≤ VIX ≤ 25), and Turbulent (VIX > 25).**
    *   Analyzes the distribution of these regimes over the sample period.

3.  **Regime-Dependent Performance Analysis**
    *   Calculates key portfolio metrics (Return, Volatility, Sharpe, Sortino, Max Drawdown, VaR, Win Rate) **for each regime separately**.
    *   Compares regime performance against unconditional, full-sample performance.
    *   **Asset-Level Analysis:** Identifies best and worst-performing assets within each regime.
    *   **Correlation Analysis:** Shows how asset correlations spike during turbulent periods, a crucial risk insight.
    *   **Beta Analysis:** Calculates regular and downside beta for each regime, highlighting assets with asymmetric risk profiles (e.g., USO).

4.  **Portfolio Optimization**
    *   Implements **Maximum Sharpe Ratio** and **Minimum Variance** portfolio optimization for each regime.
    *   Compares optimal weights across different market environments, showing how a portfolio should be structured in quiet vs. turbulent times.
    *   Introduces **practical weight constraints (e.g., max 30% per asset)** for more realistic portfolios.

5.  **Advanced Strategy & Risk Analysis**
    *   **Regime-Switching Strategy:** Backtests a dynamic strategy that uses the optimal portfolio for the identified market regime.
    *   **Tail Risk Analysis:** Analyzes the portfolio's behavior during the 20 worst market days, calculates Extreme Value at Risk (EVaR), and compares the actual return distribution to a normal distribution.
    *   **Statistical Regime Detection:** Explores alternative regime definitions based on rolling volatility and momentum, and creates a combined 2x2 regime matrix (e.g., "Goldilocks," "Crisis").

---

## 📊 Sample Key Findings

*   **Regime Matters:** The equal-weighted portfolio's annual return varies dramatically, from **+24.9% in Quiet markets to -36.2% in Turbulent markets**.
*   **Correlations are Dynamic:** The average correlation between assets jumps from ~0.30 in Normal/Quiet markets to **0.35 in Turbulent markets**, reducing the benefits of diversification exactly when it's needed most.
*   **Safe Havens Exist:** Assets like **TLT (Long-term Treasuries)** and **SHY (Short-term Treasuries)** act as strong hedges during market stress, with TLT posting a positive return on the worst market days while being negatively correlated with the S&P 500.
*   **Downside Beta Reveals Hidden Risk:** Assets like USO have a standard beta of 0.7 in turbulent markets, but their **downside beta is 1.19**. This means they become significantly more sensitive during market declines, a crucial risk factor not captured by standard models.
*   **Regime-Switching Shows Promise:** A backtested strategy that switches between regime-optimal portfolios outperforms the static equal-weight portfolio, achieving a higher total return (254.8% vs. 109.0%) and a better Sharpe ratio (0.81 vs. 0.65).

---

## 🛠️ Technologies Used

*   **Python:** Core language for analysis.
*   **Pandas & NumPy:** For data manipulation and numerical computing.
*   **Matplotlib & Seaborn:** For comprehensive data visualization.
*   **SciPy:** For scientific computing and portfolio optimization.
*   **yfinance:** For downloading financial market data.
*   **Jupyter Notebook:** For interactive development and presentation.

---

## 🚦 Getting Started

### Prerequisites

*   Python 3.9 or higher
*   pip (Python package installer)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/regime-dependent-portfolio-analysis.git
    cd regime-dependent-portfolio-analysis
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook regime_dep_port_analysis.ipynb
    ```

---

## 📝 Important Note on Backtesting Methodology

The final "Practical Regime-Switching Strategy" is backtested using **in-sample data**. The optimal portfolios for each regime were calculated using the full historical returns of that regime. This introduces a **look-ahead bias**, as future data was used to construct a portfolio applied to the past. In a real-world application, a rolling or expanding window optimization would be necessary to validate the strategy's robustness. This limitation is acknowledged here as a key area for future enhancement.

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Connect

Feel free to connect with me on [LinkedIn](your-linkedin-profile-url) or reach out via [email](your-email@example.com).
