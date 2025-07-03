# Model Card for Stock Price Factor Analysis

## Model Details

- **Model Name:** Stock Price Factor Analysis Model

## Intended Use

- **Primary Use:** To analyze factors impacting stock prices using earnings call sentiments and other financial/technical indicators.
- **Secondary Use:** To identify prominent factors influencing stock prices across different time periods (pre-COVID, COVID).
- **Out-of-Scope Use:** Not intended for direct financial advice or automated trading. This model is for research and analytical purposes only.

## Data

- **Data Sources:**
    - `data/appended_with_sentiment_features.csv`: Sentiment-related features derived from earnings call transcripts (Source: https://huggingface.co/datasets/jlh-ibm/earnings_call).
    - `data/full_stock_features.csv`: Technical indicators and stock-related features (Source: Yahoo Finance and FRED API: https://fred.stlouisfed.org/docs/api/fred/).
- **Data Characteristics:**
    - Combined dataset shape: (150 entries, 159 features).
    - Features include: Earnings Call Sentiment Features, Technical Indicators (Price & Volume Features), Quarterly or annual financials, Social Media & News Sentiment, Market & Macro Features, Calendar & Event Features.
    - Time periods analyzed: Pre-COVID (up to Dec 31, 2019) and COVID (Jan 1, 2020, to Sep 17, 2020).
- **Data Preprocessing:**
    - Merged datasets on `company` (ticker) and `date`.
    - Principal Component Analysis (PCA) applied to numerical features for dimensionality reduction.
    - Missing values in numerical features imputed using the mean.
    - Data standardized before PCA.

## Model Architecture

- **Type:** Ensemble Learning (Random Forest Regressor) and Decision Tree Regressor.
- **Components:**
    - **Dimensionality Reduction:** Principal Component Analysis (PCA).
    - **Predictive Models:** Decision Tree Regressor, Random Forest Regressor.

## Performance

- **Metrics:** Root Mean Squared Error (RMSE), R2 Score.
- **Overall Performance (using PCA-transformed features):**
    - **Decision Tree Regressor:**
        - RMSE: 349.37
        - R2 Score: 0.63
    - **Random Forest Regressor:**
        - RMSE: 354.23
        - R2 Score: 0.62

- **Period-Specific Performance (Hyperopt Optimized Random Forest):**
    - **Pre-COVID Period:**
        - Best Hyperparameters: `max_depth=9.0`, `min_samples_leaf=5.0`, `min_samples_split=10.0`, `n_estimators=50.0`
        - Best Loss (RMSE): 502.42
    - **COVID Period:**
        - Best Hyperparameters: `max_depth=8.0`, `min_samples_leaf=3.0`, `min_samples_split=10.0`, `n_estimators=170.0`
        - Best Loss (RMSE): 612.04

## Limitations

- **Data Coverage:** The analysis is limited by the available data, which extends only up to September 17, 2020. A comprehensive post-COVID analysis was not possible.
- **Generalizability:** Models are optimized for specific historical periods; their performance may vary significantly in different market conditions.
- **PCA Interpretation:** While PCA reduces dimensionality, interpreting the exact influence of original features requires further analysis of component loadings.
- **Predictive vs. Explanatory:** The models are built for prediction, but the analysis also aims to explain feature importance. However, correlation does not imply causation.

## Ethical Considerations

- **Bias:** Potential biases in the historical data, such as market anomalies or specific company events, could influence model performance and feature importance.
- **Fairness:** Not applicable as this model is for financial analysis and does not directly impact individuals or groups in a discriminatory way.
- **Transparency:** The use of PCA makes direct interpretation of original feature importance less straightforward, but component loadings are provided to enhance understanding.




