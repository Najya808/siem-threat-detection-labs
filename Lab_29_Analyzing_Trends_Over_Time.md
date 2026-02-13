# Lab 29: Analyzing Trends Over Time

## Objectives
- Understand how to work with time-series data using open-source tools.
- Learn to build and interpret time-series charts.
- Identify trends, patterns, and anomalies in data.
- Export and present data analysis results.

## Prerequisites
- Basic knowledge of data analysis and visualization.
- Familiarity with Python programming language.
- Python installed on your system.
- Jupyter Notebook or any Python IDE (VSCode, PyCharm, etc.) for running Python scripts.
- Required Python packages: `pandas`, `matplotlib`, `seaborn`.

---

## Lab Tasks

### Task 1: Importing Necessary Libraries and Loading the Dataset
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime
Load Data

# Assuming CSV file with columns: date, attempts
data = pd.read_csv('login_attempts.csv', parse_dates=['date'])
print(data.head())
Task 2: Building a Time-Series Chart
Set Date as Index

data.set_index('date', inplace=True)
Create Line Chart

plt.figure(figsize=(10, 5))
plt.plot(data.index, data['attempts'], marker='o', linestyle='-')
plt.title('Weekly Login Attempts Over Time')
plt.xlabel('Date')
plt.ylabel('Number of Attempts')
plt.grid(True)
plt.show()
Task 3: Comparing to Previous Weeks
Calculate Weekly Averages

data_weekly = data.resample('W').mean()
print(data_weekly)
Visual Comparison

plt.figure(figsize=(10, 5))
sns.lineplot(data=data_weekly, x=data_weekly.index, y='attempts', label='Weekly Average Attempts')
plt.title('Comparison of Weekly Login Attempts')
plt.xlabel('Week')
plt.ylabel('Average Attempts')
plt.grid(True)
plt.show()
Task 4: Identifying Patterns and Anomalies
Highlight Anomalies

threshold = data_weekly['attempts'].mean() + 2 * data_weekly['attempts'].std()
anomalies = data_weekly[data_weekly['attempts'] > threshold]
Plot Anomalies

plt.figure(figsize=(10, 5))
sns.lineplot(data=data_weekly, x=data_weekly.index, y='attempts')
plt.scatter(anomalies.index, anomalies['attempts'], color='red', label='Anomalies')
plt.title('Anomaly Detection in Weekly Attempts')
plt.xlabel('Week')
plt.ylabel('Average Attempts')
plt.legend()
plt.show()
Task 5: Exporting a Snapshot
plt.figure(figsize=(10, 5))
sns.lineplot(data=data_weekly, x=data_weekly.index, y='attempts')
plt.savefig('weekly_attempts_snapshot.pdf')
Conclusion
Loaded and processed time-series data using Python.

Built visualizations for analyzing weekly login trends.

Identified anomalies based on statistical thresholds.

Exported visualizations as sharable snapshots for reporting.

These skills are crucial for trend analysis, anomaly detection, and data-driven decision-making.
