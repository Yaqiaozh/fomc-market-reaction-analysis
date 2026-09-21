# Financial Market Reactions to FOMC Announcements

An event-study and exploratory machine-learning analysis of how U.S. financial markets responded to Federal Open Market Committee (FOMC) announcements from 2016 through 2025.

## Project Overview

This project examines 80 completed FOMC meetings and measures changes in:

* S&P 500 returns
* CBOE Volatility Index (VIX)
* 10-year Treasury yields
* 3-month Treasury yields
* Effective federal funds rate

The analysis combines event-study methods, statistical regression, data visualization, and classification models to evaluate short-term market reactions and explore whether pre-announcement market conditions contain information about subsequent policy actions.

## Research Questions

1. How do equity prices, volatility, and interest rates behave around FOMC announcements?
2. Do market reactions differ across Cut, Hold, and Hike decisions?
3. Were S&P 500 reactions different during the 2021–2023 high-inflation period?
4. Can pre-announcement market conditions help classify FOMC policy actions?

## Key Findings

* Financial-market indicators displayed distinct short-term movements around FOMC announcement dates.
* Market reactions varied across Cut, Hold, and Hike decisions, although their distributions overlapped substantially.
* After controlling for policy-action type, announcement-day S&P 500 returns were estimated to be 0.153 percentage points higher during the 2021–2023 high-inflation period. The difference was not statistically significant (HC3 robust p-value = 0.625).
* The majority-class baseline achieved high raw accuracy by predicting every observation as Hold, demonstrating why class-balanced evaluation metrics were necessary.
* Multinomial logistic regression achieved the strongest average cross-validation performance, with mean balanced accuracy of 0.515 and mean macro F1 of 0.469. However, performance varied considerably across folds because of the small and imbalanced sample.

## Methods

* Data cleaning and date alignment
* Event-window construction using trading days
* Exploratory data analysis and visualization
* Ordinary least squares regression with HC3 robust standard errors
* Majority-class baseline
* Multinomial logistic regression
* K-nearest neighbors classification
* Stratified train-test splitting
* Five-fold stratified cross-validation
* Confusion-matrix analysis

## Technologies

* Python
* pandas and NumPy
* Matplotlib
* statsmodels
* scikit-learn
* Jupyter Notebook

## Repository Structure

```text
fomc-market-reaction-analysis/
├── data/
│   ├── CPIAUCSL.csv
│   ├── DFF.csv
│   ├── DGS10.csv
│   ├── DTB3.csv
│   ├── FOMC_Meetings.xlsx
│   ├── SP500.csv
│   └── VIXCLS.csv
├── fomc_market_reaction_analysis.ipynb
├── requirements.txt
└── README.md
```

## How to Run

Clone or download the repository, install the required packages, and open the Notebook from the repository’s root directory.

```bash
pip install -r requirements.txt
jupyter notebook fomc_market_reaction_analysis.ipynb
```

Run all cells from top to bottom. The Notebook expects the source files to remain inside the `data` directory.

## Data Sources

Financial-market and macroeconomic data were obtained from [Federal Reserve Economic Data (FRED)](https://fred.stlouisfed.org/). FOMC meeting dates and policy-action classifications were compiled for the original academic analysis.

## Limitations

The dataset contains only 80 meetings and is imbalanced toward Hold decisions. Daily market data may also capture other news released on the same date, and the analysis does not directly measure whether each policy decision was expected by investors. Results should therefore be interpreted as descriptive and exploratory rather than causal or suitable for real-time forecasting.

Future work could incorporate intraday data, futures-implied policy expectations, and additional macroeconomic indicators.

## Project Attribution

The original academic project was completed collaboratively by **Yaqiao Zhang and Wilbur Su** for ECON 570. This repository is a reorganized and expanded portfolio version prepared by Yaqiao Zhang.
