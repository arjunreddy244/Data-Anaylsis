📊 Titanic Dataset - Exploratory Data Analysis
🔧 1. Import Libraries and Load Data
python
Copy
Edit
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('titanic.csv')
📄 2. Initial Data Exploration
python
Copy
Edit
# Overview of data
df.info()

# Statistical summary
df.describe(include='all')

# Check for null values
df.isnull().sum()

# View first few rows
df.head()
📌 Observations:

There are missing values in Age, Cabin, and Embarked.

Categorical variables include Sex, Embarked, and Pclass.

Numerical variables include Age, Fare, SibSp, Parch.

📈 3. Univariate Analysis
a. Survival Count
python
Copy
Edit
sns.countplot(x='Survived', data=df)
plt.title("Survival Count")
plt.show()
🔍 Observation: More people did not survive than survived.

b. Class Distribution
python
Copy
Edit
sns.countplot(x='Pclass', data=df)
plt.title("Passenger Class Distribution")
plt.show()
🔍 Observation: Most passengers were in 3rd class.

c. Gender Distribution
python
Copy
Edit
sns.countplot(x='Sex', data=df)
plt.title("Gender Distribution")
plt.show()
🔍 Observation: More males than females were on board.

📊 4. Bivariate Analysis
a. Survival by Gender
python
Copy
Edit
sns.countplot(x='Sex', hue='Survived', data=df)
plt.title("Survival by Gender")
plt.show()
🔍 Observation: Women had a much higher survival rate than men.

b. Survival by Class
python
Copy
Edit
sns.countplot(x='Pclass', hue='Survived', data=df)
plt.title("Survival by Class")
plt.show()
🔍 Observation: Higher class passengers had a better survival rate.

📉 5. Numerical Distribution
a. Histogram of Age
python
Copy
Edit
df['Age'].hist(bins=30)
plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Count")
plt.show()
b. Boxplot of Fare by Class
python
Copy
Edit
sns.boxplot(x='Pclass', y='Fare', data=df)
plt.title("Fare Distribution by Class")
plt.show()
🔥 6. Correlation and Heatmap
python
Copy
Edit
# Convert 'Sex' to numeric for correlation
df['Sex_num'] = df['Sex'].map({'male': 0, 'female': 1})

# Correlation matrix
corr = df[['Survived', 'Pclass', 'Sex_num', 'Age', 'Fare', 'SibSp', 'Parch']].corr()

# Heatmap
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
🔍 Observation: Survival is positively correlated with being female and fare, and negatively correlated with Pclass (lower class).

🔗 7. Pairplot
python
Copy
Edit
sns.pairplot(df[['Survived', 'Pclass', 'Sex_num', 'Age', 'Fare']], hue='Survived')
plt.show()
🧾 8. Summary of Findings
Women and children had higher survival rates.

Passengers from higher classes (1st) were more likely to survive.

Fare amount correlates with class and survival.

Age distribution shows a higher concentration of young adults.

Strong negative correlation between survival and being in 3rd class.


