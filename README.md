# 📘 Exploratory Data Analysis (EDA) – Full Guide with Visualizations
-----
## 🎯 What is EDA?
**Exploratory Data Analysis (EDA)** is the process of analyzing datasets to summarize their main characteristics, often using visual methods. It is one of the first steps in any data science or machine learning project and is used to:

- Understand the structure of the data
- Detect outliers and anomalies
- Identify patterns and trends
- Check assumptions for modeling
- Discover relationships between variables
- Handle missing data and clean the dataset
-----
## 📂 Why is EDA Important?
EDA helps to:

- Decide which features are important
- Guide feature engineering
- Determine the appropriate modeling techniques
- Avoid data leakage and wrong assumptions
-----
## 🧰 Tools & Libraries for EDA
In Python, the most commonly used libraries for EDA are:

- **pandas** – for data manipulation
- **numpy** – for numerical operations
- **matplotlib** – for static plotting
- **seaborn** – for statistical data visualization
-----
## 📊 Types of Visualizations and Their Purpose
### 1️⃣ Histogram
- **What it is**: A graph that shows the distribution of a numerical feature.
- **Use case**: Understand data distribution, skewness, modality.
- **Code**:
~~~ python
sns.histplot(df['Age'], kde=True)
~~~
### 2️⃣ Bar Plot
- **What it is**: Compares values of a numerical feature across categories.
- **Use case**: Comparing group means.
- **Code**:
~~~ python
sns.barplot(x='Pclass', y='Fare', data=df)
~~~
### 3️⃣ Box Plot
- **What it is**: Shows the distribution of a feature using quartiles and outliers.
- **Use case**: Spotting outliers and comparing distributions.
- **Code**:
~~~ python
sns.boxplot(x='Survived', y='Age', data=df)
~~~
### 4️⃣ Count Plot
- **What it is**: Displays count (frequency) of categories.
- **Use case**: Understand distribution of categorical variables.
- **Code**:
~~~ python
sns.countplot(x='Sex', data=df)
~~~
### 5️⃣ Pair Plot
- **What it is**: A matrix of scatter plots between all pairs of numeric features.
- **Use case**: Visualize relationships and separation by category.
- **Code**:
~~~ python
sns.pairplot(df[['Age', 'Fare', 'Pclass', 'Survived']], hue='Survived')
~~~
### 6️⃣ Heatmap
- **What it is**: A colored matrix showing correlation between numerical features.
- **Use case**: Detecting multicollinearity and relationships.
- **Code**:
~~~ python
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
~~~

-----
## 🧠 Summary of Visualizations

|Visualization|Purpose|Variable Type|
| :-: | :-: | :-: |
|Histogram|Distribution, skewness|Numeric|
|Box Plot|Outliers, quartiles, median|Numeric|
|Count Plot|Frequency of categorical features|Categorical|
|Bar Plot|Compare average values across categories|Categorical + Numeric|
|Pair Plot|Pairwise relationships, clustering|Numeric + Categorical|
|Heatmap|Correlation strength|Numeric|

-----
## 🧼 Common EDA Steps
1. Load the dataset
1. Understand structure (shape, types, head)
1. Identify and handle missing values
1. Univariate analysis
1. Bivariate and multivariate analysis
1. Visualize distributions and relationships
1. Summarize key insights
-----
## ✅ Final Notes
EDA is not just about making charts—it's about **asking questions and getting to know your data**. It informs decisions for the next stages, whether it's feature selection, model choice, or data preprocessing.

Always remember:
> "A picture is worth a thousand words, but an insight is worth a thousand pictures."

-----

# 📘 Titanic Dataset - Exploratory Data Analysis (EDA)
-----
## 🎯 Objective
The objective of this EDA task is to explore and analyze the Titanic dataset using Python libraries such as Pandas, Seaborn, and Matplotlib. The aim is to:

- Understand the structure and contents of the dataset.
- Identify and handle missing data.
- Detect outliers and data skewness.
- Generate statistical summaries.
- Visualize relationships between variables.
- Extract meaningful insights.
-----
## 🧰 Libraries Used
- `pandas`: for data manipulation and analysis
- `numpy`: for numerical operations
- `matplotlib.pyplot`: for plotting graphs
- `seaborn`: for advanced visualizations and statistical plots
~~~ python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

sns.set(style="whitegrid")
~~~

-----
## 📥 Loading the Dataset
~~~ python
df = pd.read_csv("Titanic.csv")
df.head()
~~~

-----
## 📝 Initial Data Exploration
### Dataset Info
~~~ python
df.info()
~~~
### Summary Statistics
~~~ python
df.describe()
~~~
### Checking Missing Values
~~~ python
df.isnull().sum()
~~~

-----
## 🧹 Data Cleaning
- Fill missing values:
~~~ python
df['Age'].fillna(df['Age'].median(), inplace=True)
df['Embarked'].fillna(df['Embarked'].mode()[0], inplace=True)
~~~

- Drop unnecessary column if exists:
~~~ python
if 'Cabin' in df.columns:
    df.drop(columns='Cabin', inplace=True)
~~~

-----
## 📊 Data Visualization in EDA – Full Explanation & Code
### 1️⃣ Histogram
A histogram shows the distribution of numerical data using bins.
~~~ python
sns.histplot(df['Age'], kde=True, bins=30, color='skyblue')
plt.title("Distribution of Age")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.show()
~~~

(image-3.png)

### 2️⃣ Bar Plot
Bar plots are used to compare average numeric values across categories.
~~~ python
sns.barplot(x='Pclass', y='Fare', data=df, palette='Blues')
plt.title("Average Fare by Passenger Class")
plt.show()
~~~

(image-4.png)

### 3️⃣ Box Plot
Box plots display the spread and outliers of numeric data.
~~~ python
sns.boxplot(x='Survived', y='Age', data=df)
plt.title("Age Distribution by Survival Status")
plt.show()
~~~

(image-1.png)


### 4️⃣ Count Plot
Count plots display the count of observations in each categorical bin.
~~~ python
sns.countplot(x='Sex', data=df)
plt.title("Passenger Count by Gender")
plt.show()
~~~

(image-2.png)

### 5️⃣ Pair Plot
Pair plots show pairwise relationships in a dataset.
~~~ python
sns.pairplot(df[['Age', 'Fare', 'Pclass', 'Survived']], hue='Survived')
~~~
(image-5.png)

### 6️⃣ Heatmap (Correlation Matrix)
Heatmaps are used to visualize correlations between numeric features.
~~~ python
plt.figure(figsize=(10, 6))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
~~~

(image-6.png)

-----
## 🧠 Summary Table

|Plot Type|Best For|Variable Types|
| :-: | :-: | :-: |
|Histogram|Data distribution, skewness, outliers|Numeric|
|Boxplot|Spread, IQR, median, outliers|Numeric|
|Countplot|Category frequencies|Categorical|
|Barplot|Comparing group means|Categorical + Numeric|
|Pairplot|Pairwise relationships + class separation|Numeric|
|Heatmap|Correlation matrix between numeric features|Numeric|

-----
## 🔍 Insights Example
- Females had higher survival rates than males.
- Passengers in 1st class were more likely to survive.
- Fare is positively skewed with some extreme values.
- Age has some missing values and slight right skewness.
-----
## ✅ Conclusion
This EDA process helps understand the dataset’s structure, detect data quality issues, and discover relationships between variables. These insights are crucial for data preprocessing and model building in the next steps of any data science or machine learning project.
