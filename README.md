# Titanic-Dataset-EDA
# 🚢 Titanic Survival Analysis - Exploratory Data Analysis (EDA)

Step-by-step Exploratory Data Analysis (EDA) on the Titanic dataset using **Python**, **Pandas**, and **Matplotlib**, generating visual insights and a PDF report.

---

## 📌 Overview
This project explores the famous Titanic passenger dataset to find survival patterns based on demographic and travel information.  
The analysis is done in **Jupyter Notebook** and produces:
- Descriptive statistics
- Missing value analysis
- Visualizations (histograms, boxplots, bar charts, correlation matrix)
- A **PDF report** summarizing the findings

---

## 📂 Dataset Information
- **Source:** [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic)
- **Rows:** 891
- **Columns:** 12
- **Target variable:** `Survived`  
  `0` = Did not survive, `1` = Survived

---

## 📊 Key Findings from EDA
- **Overall survival rate:** 38.38%
- **By Sex:**
  - Female → 74.20%
  - Male → 18.89%
- **By Passenger Class:**
  - 1st Class → 62.96%
  - 2nd Class → 47.28%
  - 3rd Class → 24.24%
- **Other Observations:**
  - Females and wealthier passengers had higher survival rates.
  - Younger passengers had slightly better survival chances.
  - Fare distribution is right-skewed — high fares link to survival.
  - Cabin information is mostly missing and should be converted to a binary feature (`HasCabin`).

---

## 🧹 Missing Values
| Column   | Missing Count |
|----------|---------------|
| Age      | 177           |
| Cabin    | 687           |
| Embarked | 2             |

---

## 🛠 Technologies Used
- **Python 3.x**
- **Pandas** (Data manipulation)
- **NumPy** (Numerical computations)
- **Matplotlib** (Data visualization)
- **Jupyter Notebook** (Interactive development)
- **FPDF** (PDF report generation)

---

## 📜 Step-by-Step Code Workflow

### **1️⃣ Import Libraries & Load Dataset**
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from pandas.plotting import scatter_matrix

df = pd.read_csv("Titanic-Dataset.csv")
df.head()

2️⃣ Dataset Info & Summary
print("Shape:", df.shape)
df.info()
df.describe(include='all').T

3️⃣ Missing Values
missing = df.isnull().sum().sort_values(ascending=False)
missing

4️⃣ Categorical Counts
for col in ['Survived', 'Pclass', 'Sex', 'Embarked']:
    print(df[col].value_counts(dropna=False))
    print(df[col].value_counts(normalize=True) * 100)

5️⃣ Visualizations
Age distribution
Fare distribution
Boxplot of Age vs Survival
Survival rate by Sex
Survival rate by Pclass
Correlation matrix
Scatter matrix

df['Age'].dropna().hist(bins=30)
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()


