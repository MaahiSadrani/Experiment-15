## Experiment-15:
## Aim: 
Data Normalization and Data Type Conversion
## Theory:
# 1. Data Normalization
Data normalization is the process of scaling numerical values into a common range so that no feature
dominates others during analysis.
1).Min-Max Normalization:
Code Used:
df['Price_Minmax'] = (df['Price'] - df['Price'].min()) / (df['Price'].max() - df['Price'].min())
df['Price'] → Access column
.min() → Returns minimum value in column
.max() → Returns maximum value
Arithmetic operations → Apply formula element-wise
2).Z-Score Normalization (Standardization):
Code Used:
df['Units_Zscore'] = (df['Units_sold'] - df['Units_sold'].mean()) / df['Units_sold'].std()
Functions Explained:
.mean() → Calculates average (μ)
.std() → Calculates standard deviation (σ)
Helps center data around 0 with unit variance
3).Decimal Scaling:
Shift decimal point to scale values.
Code Used:
df['Price_Decimal'] = df['Price'] / 100000
Explanation:
Dividing by powers of 10 reduces magnitude
Simple and useful for large values
# 2. Data Type Conversion (Categorical → Numerical):
Machine learning models require numerical data, so categorical values must be converted.
1).Label Encoding:
Assigns a unique number to each category.
Code Used:
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['Gender_Label'] = le.fit_transform(df['Customer_Gender'])
Functions Explained:
LabelEncoder() → Creates encoder object
.fit_transform():
fit() → Learns categories
transform() → Converts to numbers
Note: May introduce unintended ordering (e.g., Male=1, Female=0)
2).One-Hot Encoding:
Creates separate binary columns for each category.
Code Used:
df_encoded = pd.get_dummies(df, columns=['Payment_Method'])
Functions Explained:
pd.get_dummies() → Converts categorical column into multiple columns
Each category becomes a column with 0 or 1
3).Dummy Encoding
Same as one-hot encoding but drops one column to avoid redundancy.
Code Used:
df_dummy = pd.get_dummies(df, columns=['Payment_Method'], drop_first=True)
Functions Explained:
drop_first=True → Removes one category to avoid multicollinearity
# 3. Working with CSV Files:
Reading Dataset:
df = pd.read_csv("file.csv")
Function Explanation:
pd.read_csv() → Loads data from CSV file into DataFrame
# 4. Important Libraries Used:
Pandas (pd)-Pandas is a powerful Python library used for data manipulation and analysis.
It provides flexible data structures like Series (1D) and DataFrame (2D), which make handling structured data very easy.
Data manipulation and analysis
Functions: DataFrame(), read_csv(), get_dummies()
NumPy (np)-NumPy (Numerical Python) is used for fast numerical computations and working with arrays.
Numerical operations (though minimally used here)
Scikit-learn-Scikit-learn is a popular library used for machine learning and data preprocessing.
Machine learning utilities
Used for LabelEncoder
## Conclusion:
Successfully implemented three normalization techniques:
Min-Max (range scaling)
Z-Score (standardization)
Decimal Scaling (magnitude reduction)
Learned how to convert categorical data into numerical form using:
Label Encoding (simple but may introduce bias)
One-Hot Encoding (more accurate representation)
Dummy Encoding (efficient version of one-hot)
Understood how preprocessing improves:
Model accuracy
Data consistency
Computational efficiency
