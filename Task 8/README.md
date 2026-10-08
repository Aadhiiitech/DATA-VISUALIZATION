# Student Performance Visualization, Demographic Analysis & Educational Insights

##  Project Overview

This project analyzes student performance using **Math, Reading, and Writing scores**.

The project studies how student scores are related to:

* Parental level of education
* Lunch type
* Test preparation course
* Relationships between different subject scores

The project uses Python visualization libraries such as **Pandas, Matplotlib, and Seaborn**.

##  Objectives

* Compare average student scores.
* Analyze parental education and lunch type.
* Compare students who completed test preparation with those who did not.
* Find relationships between Math, Reading, and Writing scores.
* Use a correlation heatmap to understand score relationships.
* Get useful educational insights from the data.

##  Dataset

The project uses the **Students Performance dataset**.

Important columns include:

* Math Score
* Reading Score
* Writing Score
* Parental Level of Education
* Lunch
* Test Preparation Course

The dataset is loaded using Pandas from the preprocessed CSV file.

##  Technologies Used

* **Python**
* **Pandas** – Data handling and analysis
* **Matplotlib** – Creating charts
* **Seaborn** – Creating statistical visualizations
* **Google Colab** – Running the project

##  Visualizations

### 1. Grouped Bar Chart

A bar chart is used to compare the average **Math, Reading, and Writing scores** based on:

* Parental level of education
* Lunch type
<img width="1182" height="590" alt="download" src="https://github.com/user-attachments/assets/20be626b-7386-42f0-b73f-aae54506539a" />

This helps understand how these factors are associated with student performance.

### 2. Box Plot – Test Preparation

Box plots are created to compare score variation between students who:

* Completed the test preparation course
* Did not complete the test preparation course

Box plots are created for:

* Math
* Reading
* Writing
<img width="850" height="547" alt="download" src="https://github.com/user-attachments/assets/d3b81d6a-7399-4af9-8e6b-e4bd4ede1fe5" />
<img width="1005" height="547" alt="download" src="https://github.com/user-attachments/assets/8281101c-c92b-43de-99eb-d81703def98d" />
<img width="1005" height="547" alt="download" src="https://github.com/user-attachments/assets/36702c47-39e0-4d30-9c38-c906def45703" />

### 3. Scatter Plots

Scatter plots are used to study relationships between:

* Math vs Reading
* Math vs Writing
* Reading vs Writing

These charts help identify whether students who perform well in one subject also tend to perform well in another subject.
<img width="695" height="547" alt="download" src="https://github.com/user-attachments/assets/4e8b1f94-7a9b-479f-95bc-bd76af97ec7a" />
<img width="695" height="547" alt="download" src="https://github.com/user-attachments/assets/4a0f0dd7-cfc4-4202-982b-ebc5b13527bc" />
<img width="695" height="547" alt="download" src="https://github.com/user-attachments/assets/e0de2842-3f42-4448-bb34-2af962989fe2" />

### 4. Correlation Heatmap

A correlation heatmap is created for:

* Math Score
* Reading Score
* Writing Score

It shows how strongly the subjects are related to each other.
<img width="643" height="528" alt="download" src="https://github.com/user-attachments/assets/f7ee1406-e08e-4835-ba47-946d320b275a" />

##  Additional Analysis

The project also calculates average scores based on:

* Lunch type
* Test preparation course
* Parental level of education

It also displays the dataset shape, overall average scores, and correlation values.

## Educational Insights

The analysis can help identify:

* Differences in performance across student groups.
* The relationship between parental education and student scores.
* Differences between students with and without test preparation.
* Strong relationships between Math, Reading, and Writing performance.
* Areas where additional academic support may be useful.

##  Policy Recommendations

Based on the analysis, educational institutions can:

1. Provide additional academic support for students with lower scores.
2. Encourage students to participate in test preparation programs.
3. Provide learning support for students from disadvantaged backgrounds.
4. Monitor differences in performance between student groups.
5. Use data analysis to improve educational planning and student support.

#Project Files

```text
Student Performance Project
│
├── StudentsPerformance_preprocessed.csv
├── task_8.ipynb
├── task_8.py
└── README.md
```

##  How to Run

1. Open **Google Colab**.
2. Upload the dataset.
3. Upload or open `task_8.ipynb`.
4. Run the Python cells step by step.
5. View the generated charts and analysis results.

##  Conclusion

This project provides a simple visualization-based analysis of student performance. It uses different charts and statistical analysis to understand the effect of **parental education, lunch type, and test preparation** and to identify relationships between **Math, Reading, and Writing scores**.

The results can help educators understand student performance and make better decisions for improving educational outcomes.
