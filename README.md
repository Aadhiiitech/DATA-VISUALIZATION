# AAPL Stock Data Analysis

## Overview

This project performs **data cleaning, analysis, and visualization of Apple (AAPL) stock data** using Python.

The project analyzes stock prices and trading volume to understand daily price changes, percentage returns, volume trends, unusual trading days, and return statistics.

## Objectives

- Clean and prepare stock market data
- Analyze Open, High, Low, Close, and Volume values
- Calculate daily price changes
- Calculate daily percentage returns
- Analyze trading volume trends
- Identify anomalous trading days
- Calculate mean, variance, and standard deviation of returns
- Visualize stock volume and return distributions

## Technologies Used

- Python
- Pandas
- Matplotlib
- Google Colab
- Excel

## Dataset

The project uses **AAPL stock data** stored in `AAPL.xlsx`.

The main columns used are:

- Date
- Open
- High
- Low
- Close
- Volume

## Analysis

The data is cleaned by converting columns into the correct data types and removing missing values.

The project calculates:

- **Price Delta:** Close − Open
- **Daily Return:** Percentage change in closing price
- **Volume Moving Average:** 20-day average trading volume
- **Volume Anomalies:** Detected using the IQR method
- **Return Statistics:** Mean, variance, and standard deviation

## Visualization

The project includes visualizations for:

- Trading volume trend
- 20-day moving average
- Daily return distribution

## Project Structure

```text
AAPL-Stock-Analysis/
│
├── AAPL.xlsx
├── AAPL_1.ipynb
├── aapl_1.py
└── README.md
```

## How to Run

Install the required libraries:

```bash
pip install pandas matplotlib openpyxl
```

Run the Python file:

```bash
python aapl_1.py
```

Or open `AAPL_1.ipynb` in **Google Colab** and run the cells.

## Conclusion

This project provides a simple exploratory analysis of AAPL stock data using Python. It demonstrates how financial data can be cleaned, analyzed, and visualized to understand stock price movements, returns, and trading volume patterns.
