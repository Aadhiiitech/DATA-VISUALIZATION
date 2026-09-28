# Healthcare Data Visualization, Cost Relationship & Policy Insights

##  Project Overview

This project focuses on understanding and visualizing healthcare data using Python. It analyzes patient medical conditions, insurance providers, billing amounts, hospital stay duration, patient admissions, and relationships between important numerical variables.

The project uses **Pandas, NumPy, Matplotlib, and Seaborn** for data cleaning, analysis, visualization, and generating healthcare management insights.

The analysis includes stacked bar charts, violin plots, temporal admission trends, correlation analysis, statistical summaries, and an executive summary.

##  Objectives

* Analyze patients based on medical conditions and insurance providers.
* Clean and prepare healthcare data for analysis.
* Calculate hospital stay duration.
* Compare billing amounts across medical conditions.
* Compare billing amounts across insurance providers.
* Analyze monthly and yearly patient admissions.
* Identify relationships between age, stay duration, and billing amount.
* Calculate statistical summaries for important variables.
* Generate healthcare management recommendations.

##  Dataset

The project uses a healthcare dataset containing patient and hospital-related information.

Important columns used in the analysis include:

* `Age`
* `Medical Condition`
* `Insurance Provider`
* `Billing Amount`
* `Date of Admission`
* `Discharge Date`

The dataset is loaded using Pandas and processed before visualization and analysis.

##  Technologies Used

* **Python**
* **Google Colab**
* **Pandas** – Data cleaning and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

##  Project Workflow

### 1. Import Libraries

The project imports the required Python libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

These libraries are used for data manipulation, numerical calculations, and visualization.

### 2. Load the Dataset

The healthcare dataset is loaded using Pandas:

```python
df = pd.read_csv(file_path)
```

The dataset shape and column names are then displayed to understand the data structure.

### 3. Data Cleaning

The admission and discharge dates are converted into proper datetime format.

The billing amount is converted into numeric format.

```python
df['Date of Admission'] = pd.to_datetime(
    df['Date of Admission'], errors='coerce'
)

df['Discharge Date'] = pd.to_datetime(
    df['Discharge Date'], errors='coerce'
)

df['Billing Amount'] = pd.to_numeric(
    df['Billing Amount'], errors='coerce'
)
```

These steps help prepare the data for further analysis.

### 4. Calculate Stay Duration

Hospital stay duration is calculated using the difference between discharge date and admission date.

```python
df['Stay Duration'] = (
    df['Discharge Date'] - df['Date of Admission']
).dt.days
```

Rows with negative stay duration are removed.

### 5. Remove Missing Values

Rows with missing values in important columns are removed.

The project checks:

* Medical Condition
* Insurance Provider
* Billing Amount
* Date of Admission

##  Data Visualization

### 1. Stacked Bar Chart

A stacked bar chart is created to compare the number of patients across medical conditions and insurance providers.

```python
condition_insurance = pd.crosstab(
    df['Medical Condition'],
    df['Insurance Provider']
)
```
<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/8b0baff4-b4c5-4b41-994c-dfc0724d5ef9" />

The chart shows the distribution of patients for different medical conditions and insurance providers.

### 2. Violin Plot – Medical Condition

A violin plot is used to visualize billing amount distributions for different medical conditions.

It helps understand how billing amounts are distributed within each medical condition.
<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/cc7ec1a7-f709-454f-9b5f-c2173f5cdc9a" />

### 3. Violin Plot – Insurance Provider

Another violin plot compares billing amounts across insurance providers.

This helps identify differences in billing distributions between insurance providers.
<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/3560284e-9786-452c-87d8-1e23f69613d3" />

##  Patient Admission Analysis

### Monthly Admissions

Monthly patient admissions are calculated using the admission date.

```python
monthly_admissions = (
    df.set_index('Date of Admission')
      .resample('M')
      .size()
)
```
<img width="1390" height="590" alt="download" src="https://github.com/user-attachments/assets/3ca3531c-aa58-4327-a187-d943033991a8" />

A line chart is used to visualize monthly admission patterns and identify periods with higher or lower admissions.

### Yearly Admissions

Yearly patient admissions are also calculated and visualized using a line chart.

This provides a broader view of admission patterns over different years.
<img width="989" height="490" alt="download" src="https://github.com/user-attachments/assets/c1d46dd5-cdf4-48f5-aaf7-2f2ec2a569c7" />

##  Correlation Analysis

The project analyzes the relationship between:

* Age
* Stay Duration
* Billing Amount

```python
correlation_data = df[
    ['Age', 'Stay Duration', 'Billing Amount']
]

correlation_matrix = correlation_data.corr()
```
<img width="645" height="490" alt="download" src="https://github.com/user-attachments/assets/9b04645e-ce61-48c6-bf91-a5a6a35716d1" />
<img width="555" height="451" alt="download" src="https://github.com/user-attachments/assets/ff56ff0c-6483-4a99-b664-abc5805caa96" />

A correlation heatmap is created to make these relationships easier to understand.

The correlation matrix helps identify whether numerical variables have positive, negative, or weak relationships.

##  Statistical Analysis

Descriptive statistics are calculated for:

* Billing Amount
* Stay Duration
* Age

The analysis uses:

```python
df['Billing Amount'].describe()
df['Stay Duration'].describe()
df['Age'].describe()
```

This provides measures such as count, mean, standard deviation, minimum, maximum, and quartiles.

##  Billing Analysis

### Billing by Medical Condition

The average billing amount, median billing amount, and patient count are calculated for each medical condition.

```python
condition_cost = (
    df.groupby('Medical Condition')['Billing Amount']
      .agg(['mean', 'median', 'count'])
      .sort_values('mean', ascending=False)
)
```

### Billing by Insurance Provider

Billing statistics are also calculated for each insurance provider.

```python
insurance_cost = (
    df.groupby('Insurance Provider')['Billing Amount']
      .agg(['mean', 'median', 'count'])
      .sort_values('mean', ascending=False)
)
```

##  Hospital Stay Analysis

Average and median hospital stay duration are calculated for each medical condition.

```python
stay_summary = (
    df.groupby('Medical Condition')['Stay Duration']
      .agg(['mean', 'median'])
      .sort_values('mean', ascending=False)
)
```

This provides a comparison of hospital stay duration across medical conditions.

##  Executive Summary

The project generates an executive summary containing:

* Total number of patients
* Average billing amount
* Average hospital stay duration
* Average patient age

The summary is generated directly from the cleaned dataset.

##  Healthcare Management Recommendations

The project provides the following recommendations:

1. Monitor high-cost medical conditions.
2. Analyze insurance-wise billing patterns.
3. Prepare resources during admission surges.
4. Monitor patients with long hospital stays.
5. Use admission trends for staff planning.
6. Use billing analysis for better budget planning.

These recommendations are included in the project output based on the analysis performed.

##  Key Analysis Areas

| Analysis               | Purpose                                                      |
| ---------------------- | ------------------------------------------------------------ |
| Stacked Bar Chart      | Compare patients by medical condition and insurance provider |
| Violin Plot            | Analyze billing amount distributions                         |
| Monthly Line Chart     | Analyze monthly admissions                                   |
| Yearly Line Chart      | Analyze yearly admissions                                    |
| Correlation Heatmap    | Study relationships between numerical variables              |
| Descriptive Statistics | Summarize age, billing, and stay duration                    |
| Billing Analysis       | Compare costs by condition and insurance provider            |
| Stay Analysis          | Compare hospital stay duration                               |

##  Project Structure

```text
Healthcare-Data-Visualization/
│
├── healthcare_2.ipynb
├── healthcare_2.py
├── healthcare_dataset.csv.xls
└── README.md
```

##  How to Run

### Using Google Colab

1. Open **Google Colab**.
2. Upload `healthcare_2.ipynb`.
3. Upload the healthcare dataset.
4. Update the dataset file path if required.
5. Run the cells from top to bottom.
6. View the generated charts and analysis results.

### Using Python

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn
```

Then run:

```bash
python healthcare_2.py
```

##  Conclusion

This project provides a complete healthcare data analysis workflow, starting from data loading and cleaning and continuing through visualization, statistical analysis, correlation analysis, billing analysis, hospital stay analysis, and management recommendations.

The visualizations help understand patient admission patterns and billing distributions, while the statistical and correlation analyses provide additional information about healthcare costs, patient age, and hospital stay duration.

##  Project Type

**Healthcare Data Understanding, Visualization, Cost Relationship & Policy Insights**

##  License

This project is created for educational and academic purposes.
