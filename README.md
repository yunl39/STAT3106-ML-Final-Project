# STAT3106-ML-Final-Project
## Summary
This project explores the use of Reddit sentiment data and financial indicators to predict the daily return direction of small-cap stocks from 2022 to 2024. We implemented machine learning models including Random Forest, XGBoost, and Elastic Net, using a variety of features such as Reddit sentiment scores, macroeconomic indicators, and technical stock metrics. Despite extensive experimentation, the models achieved only modest predictive accuracy (55–65%). A simulated trading strategy based on the model reduced losses compared to random guessing, although it did not yield profits. This work highlights the need for more robust sentiment features and improved alignment between social discourse and market outcomes.

## Explanation of the folders
### 📂 Data Ingestion, Feature Generation & EDA
#### 🧠 Reddit Data Processing

- **`redditdata.ipynb`** and **`all_data.ipynb`**  
  These notebooks parse raw Reddit `.zst` archives, filter for quality, and produce a cleaned dataset of ~92,000 posts across six finance-related subreddits. 
#### 📉 Stock Data & EDA
- **`stock&EDA.ipynb`**  
  Retrieves historical stock price and volume data via the Yahoo Finance API. Also performs return diagnostics, quality checks, and basic EDA. Includes visualizations of returns and their correlation with Reddit sentiment features.

#### 💬 Reddit Feature Engineering & EDA
- **`Redditfeature&EDA.ipynb`**  
  Generate Reddit-based features like daily sentiment scores (overall, sector, and firm-level) and mention frequencies. Performs EDA to examine trends, skewness, and potential predictive value of these features.

## 📂 Models
- **`modelwithoutreddit.ipynb`**  
  Contains the baseline modeling pipeline that excludes all Reddit-related features. This serves as a benchmark to evaluate the added value of sentiment data.

- **`Models.ipynb`**  
  Includes the complete modeling workflow with Reddit sentiment features, feature transformations, model training, performance comparison, and final trading simulation.
---
Each component is designed to support downstream modeling and analysis in a structured and reproducible way.

## 📊 Data Sources

### 📈 Stock Data
Stock data was retrieved using the [Yahoo Finance API](https://finance.yahoo.com/), which includes historical stock prices, trading volume for the selected small-cap stocks.

### 📈 Macroeconomic Indicators
- **Expected Inflation (5-Year)**: [EXPINF5YR – Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/EXPINF5YR)  
- **Federal Funds Rate**: [DFF – Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/DFF)  
- **Real Gross Domestic Product (GDP)**: [GDPC1 – Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/GDPC1)  
- **Consumer Price Index (CPI)**: [FRBC Economic Commentary](https://doi.org/10.26509/frbc-ec-201002)  
- **Industrial Production Index**: [INDPRO – Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/INDPRO)

### 💬 Reddit Data
Reddit post data was sourced from [Academic Torrents](https://academictorrents.com/details/1614740ac8c94505e4ecb9d88be8bed7b6afddd4), which provides compressed `.zst` files containing full Reddit submissions. We parsed these files using the Python scripts from the [PushshiftDumps GitHub repository](https://github.com/Watchful1/PushshiftDumps).

We extracted posts from six finance-focused subreddits:
- `r/investing`
- `r/stocks`
- `r/wallstreetbets`
- `r/StocksAndTrading`
- `r/stockstobuytoday`
- `r/investingforbeginners`

We restricted our dataset to posts created between **January 1, 2022** and **December 31, 2024**. For each post, we collected:
- Full post content
- Number of comments
- Score (engagement metric)
- Upvote ratio
- Creation timestamp

The initial extraction yielded approximately **266,000** posts. After filtering out entries with incomplete content, we retained **92,237** high-quality posts. All downstream analysis and modeling are based on this cleaned dataset.
