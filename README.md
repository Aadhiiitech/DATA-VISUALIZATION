# Healthcare Data Understanding, Cleaning & Exploratory Analysis

## Project Overview

This project focuses on understanding, cleaning, analyzing, and visualizing a healthcare dataset.

The main purpose of this project is to:

* Understand the healthcare dataset
* Handle missing values
* Clean categorical data
* Convert date columns into proper date format
* Calculate hospital stay duration
* Categorize patients based on admission urgency
* Calculate billing statistics
* Analyze patient demographics by medical condition
* Create charts for better understanding of the data

---

## Dataset

The project uses a healthcare dataset containing information about patients, medical conditions, admission details, billing amounts, and hospital stay dates.

### Important Columns

* Name
* Age
* Gender
* Medical Condition
* Date of Admission
* Discharge Date
* Admission Type
* Billing Amount

The dataset is loaded using Pandas.

```python
df = pd.read_csv('/content/healthcare_dataset.csv.xls')
```

The dataset shape, column names, and first five records are displayed before performing the analysis.

---

## Technologies Used

* Python
* Google Colab
* Pandas
* Matplotlib

---

## Project Workflow

### 1. Import Libraries

The project uses Pandas for data analysis and Matplotlib for visualization.

```python
import pandas as pd
import matplotlib.pyplot as plt
```

---

### 2. Load the Dataset

The healthcare dataset is loaded into a Pandas DataFrame.

```python
df = pd.read_csv('/content/healthcare_dataset.csv.xls')
```

The following information is checked:

* Dataset shape
* Column names
* First five records

---

### 3. Check Missing Values

Missing values are identified using:

```python
df.isnull().sum()
```

This helps to understand which columns contain missing data.

---

### 4. Handle Missing Categorical Values

All categorical columns are identified and missing values are replaced with `"Unknown"`.

```python
categorical_cols = df.select_dtypes(include='object').columns

for col in categorical_cols:
    df[col] = df[col].fillna('Unknown')
```

This prevents missing categorical values from causing problems during analysis.

---

### 5. Handle Missing Billing Amounts

Missing values in the `Billing Amount` column are replaced using the median billing amount.

```python
df['Billing Amount'] = df['Billing Amount'].fillna(
    df['Billing Amount'].median()
)
```

Using the median helps provide a reasonable value without being strongly affected by extreme billing amounts.

---

### 6. Convert Date Columns

The admission and discharge date columns are converted into proper datetime format.

```python
df['Date of Admission'] = pd.to_datetime(
    df['Date of Admission'], errors='coerce'
)

df['Discharge Date'] = pd.to_datetime(
    df['Discharge Date'], errors='coerce'
)
```

Invalid date values are converted to missing values instead of causing errors.

---

### 7. Fill Missing Dates

Forward filling is used to handle missing admission and discharge dates.

```python
df['Date of Admission'] = df['Date of Admission'].ffill()
df['Discharge Date'] = df['Discharge Date'].ffill()
```

---

### 8. Calculate Hospital Stay

A new feature called `Hospital Stay Days` is created.

```python
df['Hospital Stay Days'] = (
    df['Discharge Date'] - df['Date of Admission']
).dt.days
```

This calculates the number of days each patient stayed in the hospital.

---

### 9. Hospital Stay Statistics

Descriptive statistics are calculated for hospital stay duration.

```python
df['Hospital Stay Days'].describe()
```

This provides information such as:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

---

### 10. Clean Admission Type

Admission type values are standardized using `strip()` and `title()`.

```python
df['Admission Type'] = df['Admission Type'].str.strip().str.title()
```

This makes values consistent for analysis.

---

### 11. Categorize Admission Urgency

A new column called `Urgency Category` is created.

The admission categories are:

* Emergency
* Urgent
* Elective

```python
df['Urgency Category'] = df['Admission Type'].replace({
    'Emergency': 'Emergency',
    'Urgent': 'Urgent',
    'Elective': 'Elective'
})
```

The number of patients in each category is then calculated.

---

## Billing Amount Analysis

The project calculates descriptive statistics for patient billing amounts.

```python
df['Billing Amount'].describe()
```

The following statistics are also calculated:

### Mean

```python
df['Billing Amount'].mean()
```

### Median

```python
df['Billing Amount'].median()
```

### Standard Deviation

```python
df['Billing Amount'].std()
```

These statistics help understand the distribution and variation of healthcare billing amounts.

---

## Demographic Analysis by Medical Condition

Patients are grouped according to their medical condition.

The analysis calculates:

* Number of patients
* Average age
* Male patients
* Female patients
* Average billing amount
* Average hospital stay

```python
demographics = df.groupby('Medical Condition').agg(
    Patients=('Name', 'count'),
    Average_Age=('Age', 'mean'),
    Male=('Gender', lambda x: (x == 'Male').sum()),
    Female=('Gender', lambda x: (x == 'Female').sum()),
    Average_Billing=('Billing Amount', 'mean'),
    Average_Stay=('Hospital Stay Days', 'mean')
)
```

This provides a summarized view of patient demographics for each medical condition.

---

# Data Visualization

Matplotlib is used to create different charts.

## 1. Patients by Medical Condition

A bar chart is created to show the number of patients for each medical condition.

```python
condition_count = df['Medical Condition'].value_counts()

condition_count.plot(kind='bar')
```

### Purpose

This chart helps identify how many patients belong to each medical condition.
<img width="859" height="532" alt="download" src="https://github.com/user-attachments/assets/4871cd5f-6d4c-4714-8b9b-16ac3149ff03" />

---

## 2. Admission by Urgency

A bar chart shows the number of patients for each admission urgency category.

```python
df['Urgency Category'].value_counts().plot(kind='bar')
```

### Categories

* Emergency
* Urgent
* Elective

This helps understand the distribution of patient admission types.
<img width="635" height="470" alt="download" src="https://github.com/user-attachments/assets/4d10c900-8065-4781-81be-197f8e933d5d" />

---

## 3. Billing Amount Distribution

A histogram is created to understand the distribution of billing amounts.

```python
plt.hist(df['Billing Amount'], bins=30)
```

### Purpose

The histogram helps identify:

* Common billing ranges
* Distribution pattern
* Possible extreme values
<img width="704" height="470" alt="download" src="https://github.com/user-attachments/assets/2fb10c27-8679-4cae-a240-c237b5719623" />

---

## 4. Hospital Stay Distribution

A histogram is also created for hospital stay duration.

```python
plt.hist(df['Hospital Stay Days'], bins=20)
```

### Purpose

This visualization helps understand how long patients generally stay in the hospital.
<img width="704" height="470" alt="download" src="https://github.com/user-attachments/assets/9577bc02-c210-4926-af60-f221352a90bf" />

---

# Final Dataset

After cleaning and feature creation, the final dataset is displayed.

```python
display(df.head())
print("Final Shape:", df.shape)
```

The final dataset contains the original information along with the newly created:

```text
Hospital Stay Days
Urgency Category
```

The final shape of the dataset is also displayed at the end of the analysis.

---

# Key Features Created

| Feature              | Description                                              |
| -------------------- | -------------------------------------------------------- |
| `Hospital Stay Days` | Number of days between admission and discharge           |
| `Urgency Category`   | Categorizes admissions as Emergency, Urgent, or Elective |

---

# Analysis Performed

The project performs the following analysis:

1. Dataset inspection
2. Missing value detection
3. Missing categorical value handling
4. Missing billing value handling
5. Date conversion
6. Missing date handling
7. Hospital stay calculation
8. Admission type cleaning
9. Admission urgency categorization
10. Billing amount statistics
11. Medical condition demographic analysis
12. Patient count analysis
13. Billing distribution visualization
14. Hospital stay distribution visualization
15. Final dataset inspection

---

# Project Structure

```text
Healthcare-Data-Analysis/
│
├── healthcare_dataset.csv.xls
├── healthcare_1.py
├── healthcare_1.ipynb
└── README.md
```

---

# How to Run

## Using Google Colab

1. Open Google Colab.
2. Upload `healthcare_1.ipynb`.
3. Upload the healthcare dataset.
4. Make sure the dataset filename matches the filename used in the code.
5. Run the cells one by one.
6. View the statistics and charts.

## Using Python

Install the required libraries:

```bash
pip install pandas matplotlib
```

Then run:

```bash
python healthcare_1.py
```

---

# Expected Output

The project produces:

* Dataset shape
* Column names
* First five records
* Missing-value information
* Hospital stay statistics
* Admission category counts
* Billing statistics
* Demographic summary by medical condition
* Patients by medical condition chart
* Admission urgency chart
* Billing amount histogram
* Hospital stay histogram
* Final cleaned dataset
* Final dataset shape

---

# Conclusion

This project demonstrates a complete basic healthcare data analysis workflow using Python.

The dataset is first inspected and cleaned. Missing values are handled, date columns are standardized, and hospital stay duration is calculated. Admission types are categorized into Emergency, Urgent, and Elective groups.

Statistical analysis is then performed on billing amounts and hospital stays. Patient demographics are analyzed based on medical conditions. Finally, different visualizations are created to make the healthcare data easier to understand.

The project provides a simple foundation for healthcare data understanding, cleaning, exploratory analysis, and visualization.
