


# Optimizing Marketing Campaigns with Regression & A/B Testing

This repository demonstrates how to optimize marketing campaigns by performing **regression analysis**, **correlation analysis**, and **A/B testing** on marketing data. The goal is to derive actionable insights to enhance marketing performance, predict key metrics, and evaluate the effectiveness of different marketing strategies.

## **Table of Contents**

1. [Project Overview](#project-overview)
2. [Getting Started](#getting-started)
3. [Dataset](#dataset)
4. [Project Workflow](#project-workflow)
    - [Data Overview](#data-overview)
    - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
    - [Regression Analysis](#regression-analysis)
    - [A/B Testing](#ab-testing)
5. [Model Performance Evaluation](#model-performance-evaluation)
6. [Insights and Recommendations](#insights-and-recommendations)
7. [Future Work](#future-work)
8. [Conclusion](#conclusion)

## **Project Overview**

In this project, we explore the relationship between marketing metrics such as **user sessions**, **bounce rates**, **income**, and **conversions**. By employing **regression analysis**, we aim to predict conversion rates based on these features. We also utilize **correlation analysis** to uncover relationships between variables, helping to identify which factors significantly influence conversions. Additionally, **A/B testing** is implemented to compare different marketing strategies and evaluate their effectiveness.

### **Key Features:**
- **Regression Analysis**: Linear regression is used to model the relationship between independent variables (like income, user sessions, and bounce rates) and a dependent variable (conversions). 
- **Correlation Analysis**: A correlation matrix helps identify which variables have the strongest relationships with the target variable. This allows us to understand dependencies between features, which can guide marketing decisions. 
- **A/B Testing**: We conduct an A/B test to evaluate the performance of two different marketing campaigns and assess whether the difference is statistically significant. 
- **Data Visualization**: Various plots and charts help visualize key metrics, including income distribution, conversion rates, and residuals from the regression model.

## **Getting Started**

To get started with this project, follow the instructions below to set up the environment and run the analysis.

### **Prerequisites**
Ensure the following Python libraries are installed to run the analysis:

- `pandas`: Data manipulation and analysis.
- `numpy`: Numerical computing.
- `matplotlib`: Visualization library for creating static, animated, and interactive plots.
- `seaborn`: Advanced statistical data visualization.
- `scipy`: Scientific and technical computing.
- `sklearn`: Machine learning library for regression and model evaluation.

Install the necessary libraries with the following:

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

### **Dataset**
This project uses a marketing sales analysis dataset, containing various features related to digital marketing campaigns. Ensure to update the path to match your local dataset.

```python
data = pd.read_excel("path_to_your_data.xlsx")
```

## **Project Workflow**

1. **[Data Overview](#data-overview)**:
   - Load the dataset and get an overview using `data.head()`, `data.info()`, and `data.describe()`.
   - Check for missing values and handle them (either by dropping or imputing).
   - Clean column names by stripping extra spaces.

2. **[Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)**:
   - Visualize the distribution of income, spending, and other relevant features.
   - Identify the relationships between key metrics using correlation analysis.
![image](https://github.com/user-attachments/assets/557efb38-5fdb-41a6-bf65-49bf4190ad92)

3. **[Regression Analysis](#regression-analysis)**:
   - Train a linear regression model to predict conversions based on selected features.
![image](https://github.com/user-attachments/assets/af2f3c81-2e87-4f8a-b804-15c5d3979492)
   - Evaluate the model using metrics like Mean Squared Error (MSE) and R-squared.
   - Visualize actual vs. predicted conversions and residuals.


![image](https://github.com/user-attachments/assets/03d9f8b4-7857-4ee4-ad55-a87624d08a91)

4. **[A/B Testing](#ab-testing)**:
   - Split the data into two groups (A and B).
   - Conduct a t-test to determine if there is a significant difference between the conversion rates of the two groups.
   - Visualize the conversion rates and their distributions.
     
![image](https://github.com/user-attachments/assets/01542c1e-a433-4bbe-ac2b-7cee2dd4de00)

## **Model Performance Evaluation**

**Regression Model Evaluation**:

- **Model Coefficients**:
   - The coefficients from the linear regression model represent how much the target variable (Conversions) is expected to change with a one-unit increase in each feature while keeping other features constant:
     - `Users`: -0.039
     - `New Users`: 0.037
     - `Sessions`: -0.252
   
- **Model Intercept**: 3.64 (This is the baseline value for conversions when all features are zero).
- **Mean Squared Error (MSE)**: 12.65, which indicates the average squared difference between the predicted and actual conversion values.
- **R-squared Value**: 0.021, which indicates a very weak relationship between the selected features and conversions. This suggests that our current model doesn't explain much of the variation in conversions.

**Regression Insights**: The low R-squared value suggests that the chosen features (Users, New Users, and Sessions) are not strongly predictive of conversions. Further feature engineering or more advanced modeling techniques might be needed to improve performance.

## **Correlation Matrix**

```plaintext
                        Users  New Users  Sessions  Bounce Rate  Pages / Session  Avg. Session Duration  Conversions
Users                  1.000000   0.999443   0.999890   -0.202246    -0.138839          -0.038053            0.166905
New Users              0.999443   1.000000   0.999041   -0.201985    -0.140959          -0.037680            0.166510
Sessions               0.999890   0.999041   1.000000   -0.037464    -0.137376          -0.037464            0.167476
Bounce Rate           -0.202246  -0.201985   -0.037464   1.000000     0.129542          -0.133607           -0.009889
Pages / Session       -0.138839  -0.140959   -0.137376   0.129542     1.000000           0.467663           -0.036685
Avg. Session Duration -0.038053  -0.037680   -0.037464   -0.133607    0.467663           1.000000           -0.028883
Conversions            0.166905   0.166510   0.167476   -0.009889    -0.036685          -0.028883            1.000000
```

- **Key Insights from Correlation**:
   - The variables `Users`, `New Users`, and `Sessions` have high positive correlations with each other, which might indicate multicollinearity.
   - **Avg. Session Duration** and **Pages / Session** are more strongly correlated with **Bounce Rate**.
   - **Conversions** shows a weak positive correlation with **Users**, **New Users**, and **Sessions**, which aligns with the regression model findings.

## **A/B Testing Results**

We conducted an **A/B test** to compare the conversion rates of two groups (Group A and Group B).


- **Conversion Rates**:
   - Group A: 4.02
   - Group B: 3.94

- **T-test Results**:
   - **T-statistic**: 0.43
   - **P-value**: 0.67

**A/B Testing Insights**: 
- Since the p-value is greater than 0.05, there is **no statistically significant difference** between the conversion rates of Group A and Group B. This suggests that the changes between the two groups did not lead to a meaningful improvement in conversions.
![image](https://github.com/user-attachments/assets/7a7a181e-4563-4c58-b02b-5f65fc5b29cd)
## **Insights and Recommendations**

- **Regression Analysis Insights**: The weak predictive power of the current model highlights the need for further feature exploration or more complex modeling techniques.
- **A/B Testing Insights**: The A/B testing did not reveal a significant difference in conversion rates, which suggests that the variations in the campaigns may not have been impactful enough. Consider refining the experimental design or testing with a larger sample size.

## **Future Work**

- Implement more advanced models like **Random Forests** or **XGBoost** to improve prediction accuracy.
- Conduct additional feature engineering or experiment with other marketing variables.
- Perform deeper analysis of customer segmentation for personalized marketing strategies.

## **Conclusion**

This project combines **statistical analysis** and **machine learning** to drive actionable insights for optimizing marketing campaigns. By leveraging data, we can make data-driven decisions that enhance the effectiveness of marketing strategies, ultimately leading to better campaign performance and higher conversions.

---

