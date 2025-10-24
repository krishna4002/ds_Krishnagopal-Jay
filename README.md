# relationship between trader behavior and market sentiment

## Project Overview

This project is a data science assignment focused on analyzing the relationship between **Web3 trading behavior** and **market sentiment**, as proxied by the **Fear & Greed Index**.

The core task involves cleaning and aggregating granular historical trading data, merging it with daily sentiment classifications, and summarizing key trading metrics (volume, trades, PnL, leverage) across different market sentiment regimes.

---

## Data Sources

The analysis uses two primary datasets, which are expected to be present in the project directory:

1.  **`historical_data.csv`**: Contains granular, per-trade execution records.
    * **Key Columns:** `Account`, `Coin`, `Execution Price`, `Size Tokens`, `Size USD`, `Side`, `Timestamp IST`, `Closed PnL`, etc.
2.  **`fear_greed_index.csv`**: Contains the daily Fear & Greed Index value and its categorical classification.
    * **Key Columns:** `timestamp`, `value`, `classification`, `date`

---

## Analysis & Methodology

The complete analysis pipeline is executed in the `notebook_1 (2).ipynb` Jupyter notebook and follows these key steps:

1.  **Data Loading & Cleaning**:
    * Load both CSV files.
    * Convert raw timestamp/date columns to a standardized datetime format.
    * Extract a consistent daily `date` for aggregation.
    * Standardize trading metrics (e.g., volume, PnL) to numeric types.

2.  **Daily Aggregation**:
    * The `historical_data.csv` is grouped by the daily `date`.
    * Key daily metrics are calculated, including: `total_trades`, `unique_accounts`, `total_volume`, `avg_leverage`, and `total_closedPnL`.

3.  **Sentiment Merge & Summary**:
    * The daily trading aggregates are merged with the daily sentiment (`Extreme Fear`, `Fear`, `Neutral`, `Greed`, `Extreme Greed`, `Unknown`) from the Fear & Greed Index data.
    * A final summary table is created, grouping the aggregated trading metrics by the market `sentiment` to understand how trading behavior shifts across different market conditions.

4.  **Visualizations**:
    * A **Correlation Heatmap** is generated to show the relationships between numeric trading metrics (trades, volume, leverage, PnL).
    * Visualizations comparing average daily metrics across different sentiment levels are created (e.g., average PnL per sentiment category).

---

## Results and Outputs

The execution of the notebook generates the following output files:

### Data Files (in `csv_files/`)
* `daily_aggregates.csv`: Daily summary of trading activities (before sentiment merge).
* `daily_aggregates_with_sentiment.csv`: Daily trading data merged with the daily sentiment classification.
* `sentiment_level_aggregates.csv`: The final summary table showing mean trading metrics (trades, volume, PnL, leverage) for each sentiment category.

### Visualizations (in `outputs/`)
* `correlation_heatmap_colored.png`: Image file of the correlation matrix for trading metrics.
* Other PNG files for sentiment-based metric comparisons (e.g., PnL, Volume).

---

## Setup and Dependencies

To run this notebook locally, you'll need the following Python libraries:

```bash
pip install pandas numpy matplotlib seaborn
```
