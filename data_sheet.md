# Datasheet for Stock Price Factor Analysis Datasets

## 1. Dataset Overview

- **Dataset Name:** Stock Price Factor Analysis Datasets
- **Description:** This collection of datasets is used for analyzing factors impacting stock prices, combining earnings call sentiment features with various technical indicators and stock-related features.
- **Date of Creation/Last Update:** The data itself spans up to September 17, 2020.

## 2. Data Collection

- **Methodology:** The datasets were built from two primary sources:
    1.  **Earnings Call Sentiment Features:** Extracted from transcripts using NLP and sentiment analysis from the dataset `https://huggingface.co/datasets/jlh-ibm/earnings_call`.
    2.  **Technical Indicators and Stock-Related Features:** Sourced from Yahoo Finance and the FRED API (https://fred.stlouisfed.org/docs/api/fred/).
- **Collection Dates:** The data collected covers the period from at least 2015-01-14 up to 2020-09-17.

## 3. Data Composition

- **Files Included:**
    - `data/appended_with_sentiment_features.csv`: Contains sentiment-related features.
    - `data/full_stock_features.csv`: Contains technical indicators and stock-related features.
- **Combined Dataset Structure:**
    - The two datasets are merged based on `company` (ticker) and `date`.
    - Resulting combined dataset shape: (150 entries, 159 features).
- **Key Features (Examples):**
    - **Earnings Call Sentiment Features:** (e.g., positive_word_freq, avg_sentiment_neu, sentiment_volatility, etc.)
    - **Technical Indicators:** (e.g., open, high, low, close, volume, SMA_10, SMA_50, various trend, volatility, and momentum indicators like `trend_ichimoku_conv`, `momentum_kama`, `volatility_kcl`, `momentum_rsi`, `volatility_bbp`, etc.)
    - **Other Features:** Quarterly or annual financials, Social Media & News Sentiment, Market & Macro Features (e.g., CPI, unemployment), Calendar & Event Features.

## 4. Preprocessing/Cleaning

- **Merging:** Datasets were merged on `company` (ticker) and `date`.
- **Missing Values:** Missing values in numerical features were imputed using the mean of their respective columns.
- **Standardization:** Data was standardized before applying PCA.
- **Dimensionality Reduction:** Principal Component Analysis (PCA) was applied to numerical features.

## 5. Uses

- **Intended Use:** Analyzing factors impacting stock prices, identifying prominent factors across different time periods (pre-COVID, COVID), and building predictive models.
- **Potential Applications:** Academic research, financial modeling, understanding market dynamics, and feature engineering for stock prediction tasks.
- **Out-of-Scope Uses:** Not intended for direct investment advice or automated trading systems without further validation and rigorous testing.

## 6. Distribution

- **Access:** The datasets are available within the GitHub repository: https://github.com/pasupulaphani/scratch-scripts
- **License:** Not explicitly stated in the README. Users should refer to the GitHub repository for any licensing information.

## 7. Maintenance

- **Maintenance Plan:** Not explicitly stated in the README. Users should monitor the GitHub repository for updates.

