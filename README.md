# Equity Returns, Risk Diagnostics, PCA & OLS Regression

**Author:** Antonio Rainis

**Course:** MSc Financial Data Science, UCD Smurfit Business School

## Executive summary

This notebook builds a small toolkit for comparing equity return series and applying two classic
techniques from empirical finance: **Principal Component Analysis (PCA)** for index decomposition
and **OLS regression** for cross-security dependence.

**Workflow**
1. Download and compare log returns for Stellantis (STLA) and Henkel (HEN3.DE).
2. Run standard risk diagnostics: descriptive statistics, correlation, distribution shape,
   stationarity (ADF), and outlier detection (boxplots + z-score filtering).
3. Decompose a 30-stock basket of Hang Seng Index constituents with PCA and build a
   first-principal-component-weighted portfolio, then compare it against the official HSI.
4. Fit an OLS regression of AT&T (T) returns on Shell (SHEL) returns and diagnose the residuals.

**Key findings**
- Stellantis is materially more volatile than Henkel (std. dev. ~2.5% vs ~1.3% daily).


- The two stocks show only a weak positive correlation (~0.33), so they offer meaningful
  diversification benefit if held together.
- Within a 30-name Hang Seng basket, **Ali Health (0241.HK)** and **Bank of China (3988.HK)**
  load most heavily on the first principal component, meaning they drive most of the common
  variance in the basket.
- A portfolio weighted by the (absolute) first-principal-component loadings returned roughly
  **+40%** cumulatively over 2019-2024, while the official HSI *lost* roughly **25%** over the same
  window
- Shell explains only about **13.7%** of the variance in AT&T's daily returns (R² = 0.137), and the
  residual diagnostics show the relationship is real (p ≈ 0) but far too noisy to be used as a
  standalone predictive signal.

**How to reproduce:** run all cells top to bottom. Requires an internet connection (Yahoo Finance
via `yfinance`). Chart PNGs are saved into a local `charts/` folder as each figure is produced.

