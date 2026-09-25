# AAPL Stock Data Understanding, Cleaning & Exploratory Analysis

##  Project Overview

This project performs **stock market data understanding, cleaning, feature engineering, exploratory data analysis, visualization, and return analysis** using Apple Inc. (AAPL) stock data.

The analysis focuses on:

* Cleaning stock price and volume data
* Calculating daily price returns
* Studying Open, High, Low, and Close prices
* Analyzing trading volume
* Calculating 20-day and 50-day moving averages
* Understanding the distribution of daily returns
* Calculating mean, variance, and standard deviation
* Identifying high-volatility trading days
* Understanding overall stock return stability

---

##  Objectives

The main objectives of this project are:

1. Load and clean AAPL stock data.
2. Clean the `Open`, `High`, `Low`, `Close`, and `Volume` columns.
3. Convert the `Date` column into a proper date format.
4. Remove missing and duplicate records.
5. Calculate daily price return.
6. Visualize stock prices over time.
7. Analyze trading volume trends.
8. Calculate 20-day and 50-day moving averages.
9. Study the distribution of daily returns.
10. Calculate return statistics.
11. Detect high-volatility trading days.
12. Determine whether the stock returns show relatively stable or higher variation.

---

##  Dataset

The project uses AAPL stock market data stored in an Excel file.

### Important Columns

| Column   | Description                          |
| -------- | ------------------------------------ |
| `Date`   | Trading date                         |
| `Open`   | Opening price of the stock           |
| `High`   | Highest price during the trading day |
| `Low`    | Lowest price during the trading day  |
| `Close`  | Closing price of the stock           |
| `Volume` | Number of shares traded              |

The Python program reads the Excel dataset using Pandas.

---

##  Technologies Used

* **Python**
* **Google Colab**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Excel Dataset**

---

##  Libraries Used

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

Pandas is used for data processing, while Matplotlib and Seaborn are used for visualization.

---

## Data Cleaning

The following cleaning operations are performed:

### 1. Load Dataset

```python
df = pd.read_excel("/content/AAPL.xlsx")
```

### 2. Clean Column Names

```python
df.columns = df.columns.str.strip()
```

This removes unwanted spaces from column names.

### 3. Convert Numeric Columns

The following columns are converted into numeric values:

```text
Open
High
Low
Close
Volume
```

Invalid values are converted into missing values using `errors="coerce"`.

### 4. Remove Missing Values

Rows with missing values in the important stock columns are removed.

### 5. Remove Duplicate Records

Duplicate rows are removed from the dataset.

### 6. Convert Date

The `Date` column is converted into datetime format and the records are sorted by date.

---

##  Feature Engineering

### Daily Return

A new feature called `Daily_Return` is calculated.

The formula used is:

```text
Daily Return (%) =
((Close - Open) / Open) × 100
```

Python implementation:

```python
df["Daily_Return"] = (
    (df["Close"] - df["Open"]) / df["Open"]
) * 100
```

This shows the percentage change between the opening and closing price for each trading day.

---

##  Visualization

### 1. OHLC Price Chart

The project plots:

* Open price
* High price
* Low price
* Close price

against time.
<img width="1189" height="490" alt="download" src="https://github.com/user-attachments/assets/fc946776-f876-4149-abd4-afdda4c2ddd8" />

This helps understand how AAPL's stock price changes over the selected period.

---

### 2. Trading Volume Chart

Trading volume is plotted over time.

This helps identify periods with relatively high or low trading activity.
<img width="1189" height="490" alt="download" src="https://github.com/user-attachments/assets/366f4eaf-1c5b-4495-adee-69b378779abb" />

---

### 3. Moving Average Analysis

Two moving averages are calculated:

```python
df["MA_20"] = df["Close"].rolling(20).mean()
df["MA_50"] = df["Close"].rolling(50).mean()
```

The project compares:

* Daily Closing Price
* 20-Day Moving Average
* 50-Day Moving Average

Moving averages help smooth short-term price fluctuations and show broader price trends.
<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/ca696214-52eb-42f5-889c-7d19c5837849" />

---

### 4. Daily Return Distribution

A histogram with KDE is used to visualize the distribution of daily returns.

```python
sns.histplot(
    df["Daily_Return"],
    bins=30,
    kde=True
)
```

This helps understand how frequently different daily return values occur.
<img width="989" height="490" alt="download" src="https://github.com/user-attachments/assets/52535991-6472-4b06-8c07-cfccc98a32dd" />

---

##  Statistical Analysis

The project calculates three important statistical measures for daily returns.

### Mean

Mean represents the average daily return.

```python
mean_return = df["Daily_Return"].mean()
```

### Variance

Variance measures the amount of variation in daily returns.

```python
variance_return = df["Daily_Return"].var()
```

### Standard Deviation

Standard deviation measures the spread or variation of daily returns.

```python
std_return = df["Daily_Return"].std()
```

These statistics are printed as part of the return analysis.

---

##  Price Statistics

The project also calculates:

* Highest closing price
* Lowest closing price

```python
df["Close"].max()
df["Close"].min()
```

These values provide a simple summary of the closing-price range in the dataset.

---

##  Trading Volume Analysis

The project calculates:

### Average Trading Volume

```python
df["Volume"].mean()
```

### Maximum Trading Volume

```python
df["Volume"].max()
```

These values help summarize trading activity in the dataset.

---

## High-Volatility Detection

High-volatility days are identified using the standard deviation of daily returns.

The project considers a day to be high-volatility when:

```text
|Daily Return| > 2 × Standard Deviation
```

Python implementation:

```python
high_volatility = df[
    abs(df["Daily_Return"]) > 2 * std_return
]
```

The number of high-volatility days is then calculated.

For identified high-volatility records, the project displays:

* Open price
* Close price
* Daily return
* Volume

---

##  Stock Stability Analysis

The project uses standard deviation to provide a simple stability classification.

If:

```text
Standard Deviation < 2
```

the program prints:

```text
Stock Stability: Relatively stable returns.
```

Otherwise, it prints:

```text
Stock Stability: Higher variation in daily returns.
```

This classification is based only on the standard deviation calculated from the dataset.

---

##  Key Analysis Areas

The project provides information about:

### Price

* Opening price
* Highest price
* Lowest price
* Closing price

### Returns

* Daily return
* Mean return
* Return variance
* Return standard deviation

### Trend

* 20-day moving average
* 50-day moving average

### Trading Activity

* Average volume
* Maximum volume
* Volume trend

### Volatility

* High-volatility days
* Daily returns beyond ±2 standard deviations

---

##  Project Files

```text
AAPL Stock Analysis/
│
├── AAPL(2).xlsx
├── AAPL_2(1).ipynb
├── aapl_2(1).py
└── README.md
```

### File Description

| File              | Purpose                       |
| ----------------- | ----------------------------- |
| `AAPL(2).xlsx`    | AAPL stock dataset            |
| `AAPL_2(1).ipynb` | Google Colab/Jupyter Notebook |
| `aapl_2(1).py`    | Python source code            |
| `README.md`       | Project documentation         |

---

##  How to Run the Project

### Using Google Colab

1. Open Google Colab.
2. Upload the `.xlsx` dataset.
3. Upload or open the `.ipynb` notebook.
4. Make sure the Excel filename matches the filename used in the code.
5. Run the cells one by one.
6. View the generated charts and statistical results.

### Using Python

Install the required libraries:

```bash
pip install pandas matplotlib seaborn openpyxl
```

Then run:

```bash
python aapl_2.py
```

---

##  Expected Outputs

The project generates the following outputs:

1. **OHLC Price Chart**
2. **Trading Volume Chart**
3. **Closing Price with 20-Day and 50-Day Moving Averages**
4. **Daily Return Distribution**
5. **Return Statistics**
6. **Price Statistics**
7. **Trading Volume Statistics**
8. **High-Volatility Day Count**
9. **High-Volatility Records**
10. **Stock Stability Classification**

---

##  Conclusion

This project provides an exploratory analysis of AAPL stock data by combining data cleaning, feature engineering, statistical analysis, and visualization.

The analysis calculates daily returns from opening and closing prices, studies price and volume trends, applies moving averages, examines return distributions, and identifies unusually high-return-variation days using a ±2 standard deviation rule.
The project can be used as a basic **stock data analysis and exploratory data analysis (EDA) project** using Python.

---

##  Project Type

**Data Science / Data Analysis / Exploratory Data Analysis**

**Dataset:** AAPL Stock Data
**Tools:** Python, Pandas, Matplotlib, Seaborn, Google Colab
**Analysis:** Data Cleaning, Feature Engineering, Visualization, Statistics and Volatility Analysis
