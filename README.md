Chapman Wealth Management 
Target Corporation Quarterly Revenue Model

A time series regression analysis of Target Corporation's (NYSE: TGT) quarterly revenue, built as a due diligence deliverable for a wealth management investment thesis.

Overview

This project models 23 years of Target's quarterly revenue (fiscal Q4 2000 through Q4 2023) to figure out how stable and forecastable the company's revenue really is, ahead of an investment sizing decision. It's framed as a memo from a fictional research desk ("QuantFolio Solutions") to a fictional client ("Chapman Wealth Management") to give it a real advisory feel.

Data
Source: Compustat, quarterly financials (qSales_2024.csv)
Ticker: TGT (Target Corp)
Period: Fiscal Q4 2000 through Fiscal Q4 2023 (93 quarterly observations)
Unit of analysis: fiscal quarter
Target variable: saleq (quarterly revenue, $ millions)
No missing values in the sample.
Methodology

Built in Python with pandas, numpy, statsmodels, and matplotlib.

Loaded and filtered the raw dataset down to Target only, sorted by date.
Plotted raw quarterly revenue to visually confirm trend and seasonality.
Engineered three explanatory variables:
time, a sequential quarter counter (1, 2, 3, ...) to capture the underlying growth trend
holiday_q4, a dummy variable flagging Target's fiscal Q4 (Nov to Jan), which covers the holiday shopping season
covid_surge, a dummy variable flagging fiscal Q2 2020 onward, to capture the pandemic era demand shift
Fit an OLS regression (statsmodels.api.OLS) of quarterly revenue on time, holiday_q4, and covid_surge (plus a constant).
Key Findings
Term	Coefficient	Interpretation
Intercept	~$9,448M	Baseline quarterly revenue at the start of the sample
time	~$130M/quarter	Underlying organic growth per quarter
holiday_q4	~$4,835M	Revenue lift in the fiscal Q4 holiday quarter vs. a normal quarter
covid_surge	~$4,233M	Sustained revenue lift from the pandemic era onward

The model reports an R² of roughly 94.6%, and all three explanatory variables are statistically significant. The holiday quarter effect holds consistently across every year in the sample, and the COVID era lift looks like it stuck around as a structural step up rather than fading back to the pre 2020 trend.

Recommendation (from the memo)

The analysis supports confidence in Target's revenue durability, with the caveat that the model should be rerun each quarter, holding out the most recent 25% of data as an out of sample test, to confirm the elevated post pandemic base and growth rate are still holding before finalizing position sizing.

Files
Target Corporation Quarterly Revenue Model.ipynb, the analysis notebook (originally built in Google Colab)
qSales_2024.csv, quarterly sales input data (not included in this repo, sourced from Compustat)
How to Run
bash
pip install pandas numpy statsmodels matplotlib
jupyter notebook "Target Corporation Quarterly Revenue Model.ipynb"

Place qSales_2024.csv in the same directory as the notebook before running.

Limitations & Next Steps
The model is a simple linear OLS specification. It doesn't test for autocorrelation, heteroskedasticity, or structural breaks beyond the two dummy variables.
Out of sample validation (holding out the most recent 25% of quarters) hasn't been done yet and is the recommended next step before relying on the model for position sizing.
Revenue is only one input into an investment thesis. This model doesn't account for margins, guidance, or competitive dynamics.
Disclaimer

This project uses fictional firm names ("Chapman Wealth Management," "QuantFolio Solutions") for illustrative purposes. It's a portfolio/coursework piece, not investment advice.

See task progress for longer tasks.

README.md
Scratchpad
Chapman Wealth Management - Target Corporation Quarterly Revenue Model.ipynb - Colab.pdf
viewed
Uploads
Chapman Wealth Management - Target Corporation Quarterly Revenue Model.ipynb - Colab.pdf
