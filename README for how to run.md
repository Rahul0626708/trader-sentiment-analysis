# Trader Performance vs Market Sentiment Analysis

## Objective
The goal of this project is to analyze how market sentiment (Fear vs Greed) influences trader behavior and performance on the Hyperliquid platform. The analysis aims to uncover behavioral patterns and derive actionable insights that could inform smarter trading and risk-management strategies.

---

## Datasets
This project uses two datasets:

1. **Bitcoin Market Sentiment (Fear/Greed Index)**
   - Columns: timestamp, value, classification (Fear / Greed), date
   - Granularity: Daily sentiment data

2. **Historical Trader Data (Hyperliquid)**
   - Trade-level data including account, execution price, trade size, side, timestamps, PnL, fees, etc.
   - Granularity: Individual trades

---

## Methodology

### 1. Data Loading & Cleaning
- Both datasets were loaded using pandas.
- The trader dataset contained a small number of malformed rows, which were safely skipped during parsing.
- Numeric columns such as PnL, trade size, fees, and execution price were explicitly converted to numeric formats.
- Rows with invalid numeric values were removed to ensure reliable aggregation.

### 2. Data Alignment
- Timestamps were converted to datetime format.
- Both datasets were aligned at a **daily level** using date extraction.

### 3. Feature Engineering
Trader-level daily metrics were created, including:
- Daily PnL
- Win rate
- Number of trades per day
- Average trade size
- Average fees
- Long/short trade ratio

### 4. Aggregation
- Data was aggregated to a **trader-day level** (1 row per trader per day).
- Market sentiment was merged based on date.

---

## Analysis & Insights

### Performance vs Sentiment
- Traders generally experience **higher volatility and weaker average performance during Fear days** compared to Greed days.
- Win rates tend to be slightly higher during Greed periods.

### Behavioral Changes
- Trade frequency decreases during Fear periods, indicating risk-off behavior.
- Traders show a measurable shift in position-taking behavior depending on sentiment.

### Trader Segmentation
Traders were segmented into:
- High-activity vs Low-activity traders
- Consistent vs Inconsistent performers (based on win rate)

Key observation:
- High-activity traders outperform during Greed days but suffer larger losses during Fear days.

---

## Actionable Strategy Recommendations

1. **Risk Management Rule**  
   During Fear days, high-activity traders should reduce exposure and trade frequency to limit drawdowns.

2. **Selective Aggression Rule**  
   Increased trading activity during Greed periods should be limited to traders with historically consistent win rates.

---

## Tools & Technologies
- Python
- pandas, numpy
- matplotlib, seaborn
- Jupyter Notebook
- google colab

---

## How to Run
1. Clone the repository
2. Install required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn
