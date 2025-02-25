# 1. What is Data Science?
Data science is an interdisciplinary field that involves extracting actionable insights and knowledge from large volumes of data using a combination of scientific methods, algorithms, and systems. It encompasses various stages of the data lifecycle, including data collection, preprocessing, analysis, interpretation, and visualization.

# 2. What are the differentiate between Data Analytics and Data Science?
Data Analytics focuses on analyzing data to uncover meaningful insights, trends, and patterns that can help organizations make data-driven decisions. It typically involves examining historical data to understand what happened in the past and why. Data analytics techniques include descriptive and diagnostic analytics, which focus on summarizing and explaining past events or trends.

Data Science, on the other hand, encompasses a broader range of activities beyond just analysis. It involves not only analyzing data but also involves tasks such as data collection, cleaning, preprocessing, modeling, and interpretation. Data science aims to extract actionable insights from data to predict future outcomes, optimize processes, and drive decision-making. It often employs advanced techniques such as machine learning, predictive modeling, and deep learning to uncover hidden patterns and make predictions.

In essence, data analytics is a subset of data science, focusing mainly on analyzing historical data for insights, while data science covers a wider range of activities involved in extracting value from data, including analysis, modeling, and interpretation.

# 3. What are the differences between supervised and unsupervised learning?

Supervised and unsupervised learning are two primary types of machine learning approaches, each with distinct characteristics:

**Supervised Learning:**

1. In supervised learning, the algorithm learns from labeled data, where each input data point is associated with a corresponding target or outcome.
1. The goal of supervised learning is to learn a mapping function from input variables to output variables based on the labeled training data.
1. Supervised learning algorithms are trained using a dataset containing input-output pairs, and they aim to predict the output for new, unseen input data accurately.
1. Examples of supervised learning tasks include classification (where the output is categorical) and regression (where the output is continuous).
1. Common algorithms used in supervised learning include linear regression, logistic regression, decision trees, support vector machines (SVM), and neural networks.

**Unsupervised Learning:**

1. In unsupervised learning, the algorithm learns from unlabeled data, where the input data has no corresponding output labels or categories.
1. The goal of unsupervised learning is to find patterns, structures, or relationships within the data without explicit guidance.
1. Unsupervised learning algorithms explore the inherent structure of the data to identify clusters, associations, or anomalies.
1. Clustering and dimensionality reduction are typical tasks in unsupervised learning. Clustering algorithms group similar data points together, while dimensionality reduction techniques aim to reduce the complexity of the data by capturing its essential features.
1. Examples of unsupervised learning algorithms include K-means clustering, hierarchical clustering, principal component analysis (PCA), and autoencoders.

# 4. How do you handle a dataset missing several values?
There are various ways to handle missing data. You can:

1. Drop the rows with missing values.
2. Drop the columns with several missing values.
3. Fill the missing value with a string or numerical constant. 
4. Replace the missing values with the average or median value of the column. 
5. Use multiple-regression analyses to estimate a missing value.
6. Use multiple columns to replace missing values with average simulated values and random errors.
- you're considering various features to estimate the missing values. You'd simulate these values by calculating their averages and adding random errors to make them more realistic. This approach helps maintain the integrity of the data set while filling in the gaps caused by missing values.

# Handling missing values:
### 1. Imputation:

Fill in the missing values with a calculated or estimated value. This could be the mean, median, or mode of the existing values in the column.
python
Copy code
```python
# Example: Impute with the mean
mean_value = df['total_outstanding_orders'].mean()
df['total_outstanding_orders'].fillna(mean_value, inplace=True)
```
### 2. Forward Fill or Backward Fill:

Use the values from the previous or next row to fill in the missing values. This is especially useful when dealing with time-series data.
python
Copy code
```python
# Example: Forward fill
df['total_outstanding_orders'].fillna(method='ffill', inplace=True)
```
### 3. Interpolation:

Use interpolation methods to estimate missing values based on the values of neighboring data points.
python
Copy code
```python
# Example: Linear interpolation
df['total_outstanding_orders'].interpolate(method='linear', inplace=True)
```
### 4. Drop Rows:

If the missing values are limited and do not significantly impact the analysis, you might choose to simply remove the rows with missing values.
python
Copy code
```python
# Example: Drop rows with missing values
df.dropna(subset=['total_outstanding_orders'], inplace=True)
```
### 5. Advanced Imputation:

Explore more advanced imputation techniques, such as using machine learning algorithms to predict missing values based on other features in the dataset.
Remember to carefully consider the nature of your data and the potential impact of each strategy on your analysis. It's often a good practice to document the chosen approach and reasoning behind handling missing values in your dataset.

# correlation matrix

The correlation matrix is a table that shows the correlation coefficients between many variables in a dataset.

def - *Correlation coefficients quantify the strength and direction of the linear relationship between two variables. The values range from -1 to 1,* 
where:
  - (1) indicates a perfect positive linear correlation,
  - (-1) indicates a perfect negative linear correlation,
  - (0) indicates no linear correlation.
By calculating the correlation matrix, you can quickly understand how different variables in your dataset are related to each other. This is valuable for various data analysis tasks, such as:

1. **Identifying Relationships**: You can identify which variables have strong positive or negative relationships. For example, if the correlation coefficient between two variables is close to 1, it suggests a strong positive correlation, and if it's close to -1, it suggests a strong negative correlation.

1. **Multicollinearity**: In the context of regression analysis, high correlation between independent variables might indicate multicollinearity. Multicollinearity can affect the stability and interpretability of the regression coefficients.

1. **Feature Selection**: In machine learning, you might use the correlation matrix to identify and remove highly correlated features, reducing redundancy in your feature set.

1. **Data Exploration**: Exploring the correlation matrix can provide insights into the structure of the data and guide further analysis.
```python
# Calculate the correlation matrix
correlation_matrix = df.corr()

# Create a heatmap with correlation values
plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f", linewidths=.5)
plt.title('Correlation Heatmap')
plt.show()
```
![alt text](image_.png)

# Outliers or Anomalous

using the LocalOutlierFactor (LOF) algorithm from the sklearn.neighbors module to detect outliers in your dataset. Let me break down the code and explain each part:

```python
from sklearn.neighbors import LocalOutlierFactor
```

LocalOutlierFactor is a class from the scikit-learn library that implements the Local Outlier Factor algorithm for outlier detection.

```python
Instantiate the LOF Model:
model = LocalOutlierFactor()
```
You create an instance of the LocalOutlierFactor class. The default settings are used, but you can also specify parameters such as n_neighbors and contamination based on your data and requirements.

```python
#Fit the Model:
model.fit(df)
```
You fit the LOF model to your DataFrame (df). This step involves calculating the LOF scores for each data point in the dataset.

```python
#Predict Anomaly Scores:
df['lof_anomaly_score'] = model.fit_predict(df)
```

You predict the anomaly scores for each data point using the fit_predict method of the LOF model. The resulting anomaly scores are added as a new column, 'lof_anomaly_score', to your DataFrame (df).

'lof_anomaly_score', representing the anomaly scores assigned by the Local Outlier Factor algorithm. 
  - Negative scores typically indicate outliers,
  - and the more negative the score, the more likely the point is considered an outlier.
  - You can further analyze or visualize these scores to identify and understand potential outliers in your dataset.

## KNN imputer
* yet to write...

# Reality of DS/DA/ML
📊 Statistics: The Foundation of Data Science and AI

### 1. Understanding Data:

   
📈 Explores and summarizes data, offering insights into central tendencies, variability, and distribution.

### 2. Data Cleaning and Preprocessing:

   
🧹 Handles messy data, identifying missing values, outliers, and errors for improved data quality.

### 3. Descriptive Statistics:

   
📊 Provides a concise summary, aiding in initial data distribution understanding.

### 4. Inferential Statistics:

   
🧠 Enables drawing conclusions and predictions about a population based on a sample, crucial for machine learning.

### 5. Hypothesis Testing:

   
📊 Validates assumptions, compares groups, and assesses relationships' significance for informed decision-making.

### 6. Probability Theory:

   
🎲 Foundation for understanding uncertainties and randomness, crucial in machine learning algorithms.

### 7. Regression Analysis:

   
📈 Models relationships between variables, aiding predictions and understanding their strength and direction.

### 8. Classification and Clustering:

   
🧩 Underlies classification and clustering algorithms, grouping data based on similarities.

### 9. Bayesian Statistics:

   
🔄 Integral to probabilistic modeling, updating beliefs based on new evidence.

### 10. Model Evaluation and Validation:

    
📊 Evaluates machine learning model performance, ensuring reliability and generalization.

### 11. Feature Selection:

    
🎯 Identifies significant features, assisting in building effective machine learning models.

### 12. Understanding Uncertainty in AI Models:

    
❓ Provides tools to quantify and handle uncertainty, crucial in deep learning and reinforcement learning.

![image](https://github.com/VishalDeoPrasad/Data-Analysis/assets/44454324/23324b66-d669-47d2-b6b2-6f973a9035d5)
In summary, statistics is the backbone of data science, machine learning, and AI, providing essential tools to extract insights, validate assumptions, make predictions, and build robust models.
--------------------------------------------------------------------------
### Q1. What are the feature selection methods used to select the right variables?
There are two main methods for feature selection, i.e, filter, and wrapper methods.

1. Filter Methods
This involves: 
   * Linear discrimination analysis
   * ANOVA
   * Chi-Square

The best analogy for selecting features is "bad data in, bad answer out." When we're limiting or selecting the features, it's all about cleaning up the data coming in. 

2. Wrapper Methods
This involves: 
    * Forward Selection: We test one feature at a time and keep adding them until we get a good fit
    * Backward Selection: We test all the features and start removing them to see what works better
    * Recursive Feature Elimination: Recursively looks through all the different features and how they pair together

Wrapper methods are very labor-intensive, and high-end computers are needed if a lot of data analysis is performed with the wrapper method. 

### Q2. How can you avoid overfitting your model?
Overfitting refers to a model that is only set for a very small amount of data and ignores the bigger picture. There are three main methods to avoid overfitting:

   1. Keep the model simple—take fewer variables into account, thereby removing some of the noise in the training data
   1. Use cross-validation techniques, such as k folds cross-validation 
   1. Use regularization techniques, such as LASSO, that penalize certain model parameters if they're likely to cause overfitting







---------------------------------------------------------------------------

**Uni-variate**, **bi-variate**, and **multi-variate** analyses are statistical techniques used in data analysis to **understand relationships between variables**. They are not specific to AI but rather fall under the broader umbrella of statistics and data analysis. 

However, `they are often used in AI applications, particularly in machine learning and data science, to explore and understand datasets before building models or making predictions.` So, while they aren't a subset of AI per se, they are certainly tools commonly used within AI.

## What is a Statistical Test?
Statistical tests are used in Hypothesis Testing. You can use them to determine:

1. the relationships between input and output variables
1. estimate the differences between two or more groups

## What is Hypothesis Testing?
Hypothesis testing is a way for data scientists and researchers to make decisions about whether their ideas, or hypotheses, are supported by evidence from their experiments or observations.

Here's a simple breakdown:

1. **Formulate a Hypothesis**: Start with an idea or a guess about something you want to study. This is called a hypothesis.
1. **Collect Data**: Conduct experiments or gather information to see if the data supports your hypothesis.
1. **Test Your Hypothesis**: Use statistical techniques to analyze the data and determine if it provides strong evidence for or against your hypothesis.
1. **Decide a Significance Level**: Decide a significance level.
1. **Make a Conclusion**: Based on the analysis, you decide whether the data supports your original idea or if it suggests something different.

# Example 1: Hypothesis Testing for new drug

## Overview

Hypothesis testing is a fundamental concept in statistics and scientific research. It allows researchers to make decisions based on evidence gathered from experiments or observations. Here's an example to illustrate how hypothesis testing works:

## Example Scenario

Imagine a pharmaceutical company develops a new drug to treat a certain medical condition. The researchers hypothesize that patients who take the new drug will experience a reduction in symptoms compared to those who do not take the drug.

1. **Formulate a Hypothesis:** The hypothesis is that the new drug will reduce symptoms in patients with the medical condition.

2. **Collect Data:** The researchers conduct a clinical trial where they randomly assign patients to two groups: one group receives the new drug (the experimental group), and the other group receives a placebo (the control group). They collect data on the symptoms experienced by each group over a specified period.

3. **Test Your Hypothesis:** The researchers use statistical techniques to analyze the data and determine if there is a significant difference in symptom reduction between the two groups. They may use methods such as **t-tests** or **ANOVA** to compare means or **chi-square tests** to compare proportions.

4. **Decide a Significance Level:** The researchers decide on a significance level, typically denoted as alpha (α), which represents the threshold for determining whether the results are statistically significant. Common significance levels include 0.05 or 0.01.

5. **Make a Conclusion:** Based on the analysis, the researchers conclude whether the data provide strong evidence to support the hypothesis that the new drug reduces symptoms compared to the placebo. If the results are statistically significant at the chosen significance level, they may accept the hypothesis. If not, they may reject it or modify it based on the evidence.

## Conclusion

Hypothesis testing is a powerful tool that allows researchers to draw conclusions based on empirical evidence. By following a systematic process, researchers can evaluate their hypotheses and make informed decisions in various fields of study.

# Example 2: Hypothesis Testing in Market Research

## Overview

Hypothesis testing is a statistical method used in market research to make data-driven decisions about marketing strategies, product launches, or consumer behavior. Let's consider an example:

## Example Scenario

A company is launching a new product, and they want to determine if a particular marketing campaign will lead to a higher sales conversion rate compared to their previous campaign.

1. **Formulate a Hypothesis:** The hypothesis is that the new marketing campaign will result in a higher sales conversion rate than the previous campaign.

2. **Collect Data:** The company runs both the new and old marketing campaigns simultaneously in different markets or segments. They track the number of people exposed to each campaign and the resulting sales conversions.

3. **Test Your Hypothesis:** Using statistical techniques, such as hypothesis testing for proportions, the company compares the sales conversion rates between the two campaigns. They calculate p-values and confidence intervals to determine if there is a statistically significant difference in conversion rates.

4. **Decide a Significance Level:** The company decides on a significance level, such as 0.05, to determine the threshold for statistical significance.

5. **Make a Conclusion:** Based on the analysis, the company determines whether the data provide sufficient evidence to support the hypothesis that the new marketing campaign leads to a higher sales conversion rate. If the results are statistically significant at the chosen significance level, they may conclude that the new campaign is effective. If not, they may need to reevaluate their marketing strategy or conduct further research.

## Conclusion

Hypothesis testing enables companies to make informed decisions about marketing strategies and product launches by analyzing empirical data. By rigorously testing hypotheses, companies can optimize their marketing efforts and improve business outcomes.

# Example 3: Hypothesis Testing: Detective Analogy

## Overview

Hypothesis testing is akin to being a detective and using clues to decide if a suspect is guilty or not guilty. Let's explore this analogy further:

## Example Scenario

Imagine a detective investigating a crime where a suspect, Mr. X, is accused of theft. The detective needs to gather evidence to determine if Mr. X is guilty or innocent.

1. **Formulate a Hypothesis:** The hypothesis is that Mr. X is guilty of the theft.

2. **Collect Evidence:** The detective gathers evidence such as fingerprints, eyewitness testimonies, and security camera footage from the crime scene.

3. **Test Your Hypothesis:** Using the collected evidence, the detective conducts hypothesis testing to evaluate the likelihood that Mr. X is guilty. Each piece of evidence serves as a clue in the investigation. For example, fingerprints matching Mr. X's could support the hypothesis, while an alibi or contradictory testimony could cast doubt on it.

4. **Decide a Significance Level:** The detective sets a significance level, analogous to the threshold of reasonable doubt in a legal case. If the evidence meets this threshold, the hypothesis (guilt) is supported.

5. **Make a Conclusion:** Based on the analysis of the evidence, the detective decides whether there is sufficient proof to support the hypothesis of Mr. X's guilt. If the evidence is compelling and meets the significance level, the detective may conclude that Mr. X is guilty. If not, Mr. X is presumed innocent until proven otherwise.

## Conclusion

Hypothesis testing, like detective work, involves gathering and analyzing evidence to make informed decisions. By systematically evaluating hypotheses and considering the strength of the evidence, detectives (and researchers) can draw conclusions that are supported by empirical data.

# What is a Type I and Type II Error?
Type I and Type II errors are concepts related to hypothesis testing in statistics. Here's an explanation of each type with examples:

## Type I Error (False Positive):
**Definition**: Type I error occurs when we reject a true null hypothesis. In other words, we incorrectly conclude that there is an effect or difference when there isn't one.

**Symbol**: Often denoted by (α), the significance level.

**Example**:
   * Scenario: Testing a new drug's effectiveness.
   * Null Hypothesis(H0) : The drug has no effect.
   * Type I Error(α) : Concluding the drug is effective when it actually has no effect. or Concluding the person has commited a crime when he is actually innocent.

## Type II Error (False Negative):
**Definition**: Type II error occurs when we fail to reject a false null hypothesis. In this case, there is a true effect or difference, but our test fails to detect it.

**Symbol**: Often denoted by (β).

**Example**:
   * **Scenario**: Testing a new drug's effectiveness.
   * **Alternative Hypothesis(H1):** The drug has a significant effect.
   * **Type II Error(β)** : Failing to detect the drug's effectiveness when it actually has an effect. or Failing to detect the person has commited a crime when he is actually guilty.

## Relationship:
**Inverse Relationship**: There is typically an inverse relationship between Type I and Type II errors. As you decrease the likelihood of one type of error, the likelihood of the other type of error increases.
**Adjusting Significance Level**: By decreasing the significance level, the probability of Type I error decreases, but the probability of Type II error may increase.

It's crucial to strike a balance between these two types of errors based on the specific context and consequences of each error. The choice of significance level and statistical power (the ability to detect true effects) influences the likelihood of Type I and Type II errors in hypothesis testing.

# Hypothesis Testing and Errors

## What is Hypothesis Testing?

Hypothesis testing is a way for data scientists and researchers to make decisions about whether their ideas, or hypotheses, are supported by evidence from their experiments or observations. Here's a simple breakdown:

1. **Formulate a Hypothesis:** Start with an idea or a guess about something you want to study. This is called a hypothesis.
2. **Collect Data:** Conduct experiments or gather information to see if the data supports your hypothesis.
3. **Test Your Hypothesis:** Use statistical techniques to analyze the data and determine if it provides strong evidence for or against your hypothesis.
4. **Decide a Significance Level:** Decide a significance level.
5. **Make a Conclusion:** Based on the analysis, you decide whether the data supports your original idea or if it suggests something different.

## Examples of Hypothesis Testing

### Example 1: Hypothesis Testing for New Drug

- **Null Hypothesis (H0):** The new drug does not reduce symptoms in patients with the medical condition.
- **Alternative Hypothesis (H1):** The new drug reduces symptoms in patients with the medical condition.

### Example 2: Hypothesis Testing in Market Research

- **Null Hypothesis (H0):** The new marketing campaign does not result in a higher sales conversion rate compared to the previous campaign.
- **Alternative Hypothesis (H1):** The new marketing campaign results in a higher sales conversion rate compared to the previous campaign.

### Example 3: Hypothesis Testing: Detective Analogy

- **Null Hypothesis (H0):** Mr. X is not guilty of the theft.
- **Alternative Hypothesis (H1):** Mr. X is guilty of the theft.

## Type I and Type II Error Explanation

- **Type I Error (False Positive):** This occurs when we incorrectly reject the null hypothesis when it is actually true.
- **Type II Error (False Negative):** This occurs when we fail to reject the null hypothesis when it is actually false.

# What is p-value?
The p-value, short for "probability value," is a number that helps us understand the strength of evidence against a null hypothesis in hypothesis testing.

or 

* p-value quantifies the strength of evidence i.e. how likely the evidence occured by a random chance. The smaller the p-value, less likely the result occured by random change and the stronger the evidence that you should reject the null hypothesis.

* To say whether the p-value is significant or not, we need a significance threshold called the significance level. This threshold is usually set at 0.05.

* It's important because it helps control the rate of Type I errors. By setting a threshold, we define the level of evidence needed to reject the null hypothesis. Lower thresholds (e.g., 0.01) require stronger evidence.

* If the p-value is BELOW the threshold (meaning smaller than), then you can infer a statistically significant evidence i.e. outcome didn't occur randomly.
i.e. For p-value < 0.05, you can Reject the Null Hypothesis

* Otherwise, then you can infer no statistically significant evidence i.e. outcome occured at random.
i.e. For p-value > 0.05, you Fail to Reject the Null Hypothesis

**Here's a simple explanation:**

#### 1. Formulate the Hypothesis
* Null Hypothesis (H0): This is a statement that there is no significant difference or relationship. It's like assuming innocence in a court trial.

* Alternative Hypothesis (H1): This is the opposite of the null hypothesis. It suggests that there is a significant difference or relationship.
#### 2. Collect Data: Perform experiments or gather information.
#### 3. Apply an appropriate Statistical Test
* **Calculate Test Statistic**: This is a numerical value calculated from your data, depending on the type of test you're conducting (e.g., t-test, F-test, etc.).
* **Calculate p-value**: It's the probability of observing a test statistic as extreme as, or more extreme than, the one calculated from your data, assuming the null hypothesis is true.
#### 4. Decide a Significance Level
#### 5. Make a Conclusion
* if p_value < significance_level => Reject the null hypothesis (H0)
* otherwise => Fail to reject the null hypothesis (H0)

**Now, let's go through an example:**
### Example: Coin Toss
Suppose you have a coin and you want to test if it's fair (i.e., has an equal chance of landing heads or tails). Here's how hypothesis testing works:

#### 1. Formulate the Hypothesis.
* **Null Hypothesis (H0):** The coin is fair.
* **Alternative Hypothesis (H1):** The coin is not fair (meaning it's biased).
#### 2. Collect a sample.
You flip the coin 100 times and get 60 heads and 40 tails.
#### 3. You calculate a test statistic
* In this case, you might use a chi-squared test.
* Let's say the p-value you calculate is 0.03.
#### 4. Decide a significance_level (i.e. alpha = 0.05)
#### 5. Make a conclusion - 
If you set a significance level (often denoted as alpha, α) at 0.05 (5%), then your p-value of 0.03 is less than α. This means:
* If the coin were fair (null hypothesis is true), you'd expect to see results as extreme as this or more extreme only 3% of the time.
* Since 3% is less than 5%, you have enough evidence to reject the null hypothesis. You conclude that the coin is likely biased.
Remember, a small p-value indicates strong evidence against the null hypothesis, while a large p-value suggests weak evidence against it. However, a p-value alone does not prove or disprove anything; it's just part of the evidence you consider in making a decision.

# Example: Hypothesis Testing with Exam Performance

In this example, we'll illustrate how hypothesis testing can be applied to examine the difference in exam performance between two groups of students.

### Formulate the Hypothesis:
- **Null Hypothesis (H0):** There is no significant difference in exam performance between two groups of students.
- **Alternative Hypothesis (H1):** There is a significant difference in exam performance between the two groups of students.

### Collect Data:
- You administer an exam to two groups of students: Group A and Group B.

### Apply an Appropriate Statistical Test:
- You decide to perform an independent samples t-test to compare the mean scores of the two groups.

### Calculate Test Statistic:
- After grading the exams, you find that Group A has a mean score of 75, with a standard deviation of 8, and Group B has a mean score of 80, with a standard deviation of 7.

### Calculate p-value:
- Using the t-test, you calculate a p-value of 0.02.

### Decide a Significance Level:
- Let's set a significance level (alpha) at 0.05.

### Make a Conclusion:
- If there were truly no difference in exam performance between the two groups (null hypothesis is true), you'd expect to see results as extreme as this or more extreme only 2% of the time.
- Since 2% is less than 5%, you have enough evidence to reject the null hypothesis.
- Therefore, you conclude that there is a significant difference in exam performance between Group A and Group B.

# Important Hypothesis Tests

There are many hypothesis tests used in statistical analysis. Below are several important ones, categorized into univariate and bivariate tests, and further divided based on the type of data they are suitable for:

## Univariate Tests

### Tests for Categorical Data

#### Chi-Square Goodness-of-Fit Test
- **Description:** Tests whether the observed frequencies of categorical data match the expected frequencies according to a specified distribution.
- **Use:** Often used to analyze categorical data and test for goodness of fit.

### Tests for Numerical Data

#### Shapiro-Wilk Test
- **Description:** A statistical test that checks whether a dataset follows a normal distribution.
- **Use:** Useful for assessing the normality of data before applying certain statistical tests.

#### Kolmogorov-Smirnov Test
- **Description:** Tests whether a sample comes from a specific distribution (not limited to normal distribution). It can be used to compare any two continuous distributions.
- **Use:** Often used to compare the distributions of two samples.

#### One-Sample t-test
- **Description:** Tests whether the mean of a single sample is significantly different from a known or hypothesized population mean.
- **Use:** Used to determine if there is a significant difference between a sample mean and a population mean.

#### Mann-Whitney U Test (Wilcoxon Rank-Sum Test)
- **Description:** Nonparametric test that compares the medians of two independent samples.
- **Use:** Used when assumptions of normality and equal variances are violated or when dealing with ordinal or non-normally distributed data.

## Bivariate Tests

### Tests for Categorical Data

#### Chi-Square Test of Independence
- **Description:** Tests whether there is a significant association between two categorical variables in a contingency table.
- **Use:** Used to determine if there is a relationship between two categorical variables.

#### Fisher's Exact Test
- **Description:** A statistical test used to determine if there are nonrandom associations between two categorical variables when sample sizes are small.
- **Use:** Particularly useful when dealing with small sample sizes in contingency tables.

#### McNemar's Test
- **Description:** A statistical test used to determine if there are changes in proportions between two related categorical variables measured at two different time points.
- **Use:** Commonly used in before-and-after studies or in studies with paired categorical data.

#### Chi-Square Test:
* The Chi-Square test is a statistical test used to determine if there is a significant association between two categorical variables.
In the context of feature selection, the Chi-Square test can be used to assess the independence between each feature and the target variable. Features that are highly dependent on the target variable are considered more important and can be selected for further analysis.
This test is particularly useful when dealing with categorical data or when the relationship between features and the target variable is not linear.

### Tests for Numerical Data

#### Pearson Test
- **Description:** Tests whether two samples have a linear relationship.
- **Use:** Commonly used to assess the correlation between two continuous variables.

#### Two-Sample t-test
- **Description:** Compares the means of two related samples (e.g., before and after treatment) to determine if there is a significant difference.
- **Use:** Used to compare the means of two groups and assess if they are statistically different.

#### ANOVA (Analysis of Variance)
- **Description:** Compares the means of three or more independent groups to determine if there are any statistically significant differences between them.
- **Use:** Useful for comparing means across multiple groups simultaneously.
- ANOVA (Analysis of Variance): 
   * ANOVA is a statistical test used to compare the means of two or more groups to determine if there are statistically significant differences between them.
In the context of feature selection, ANOVA can be used to assess the importance of individual features by analyzing the variance between different groups or categories in the target variable.
   * Features that result in a large variance between groups and a small variance within groups are considered more important and can be selected for further analysis.

![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)

```python
import seaborn as sns
import pandas as pd

# Load the Titanic dataset directly from seaborn
titanic = sns.load_dataset('titanic')
titanic
```
![alt text](image-5.png)
# What is Univariate Analysis?
When you do analysis on single variable that is called univariate analysis. Independent analysis of single variable that is called univariate analysis.

# 1. Categorical Data
``If you have categorical data then you have only 2 option either you go for count plot/bar plot or you go for pie chart, but pie chart give you only option to see the percentage.``
1. **Count Plot:** Tell us the frequency of all the category. how many times each category appear. samething as value count.

   **Python Code**
   ```python
   import seaborn as sns
   import matplotlib.pyplot as plt

   # Create a count plot of the 'Survived' column
   sns.countplot(data=titanic, x='survived')

   # Add title and labels
   plt.title('Count Plot of Survival on the Titanic')
   plt.xlabel('Survived')
   plt.ylabel('Count')

   # Display the plot
   plt.show()
   ```
   ![alt text](image-6.png)

   **Python Code**
   ```python
   titanic.survived.value_counts().plot(kind='bar')
   ```
   ![alt text](image-7.png)

   **Q. why most of the people prefer to travel in 1st class then 2nd class. give justification.** <br> Ans -
   1. May be because of slighly difference in price of 1st and 2nd class.
   1. May be 2nd class has not much capacity 
   1. find our mean fare price to understand less people in 2nd class then 1st class

   **python code**
   ```python 
   sns.countplot(data=titanic, x='pclass')
   ```
   ![alt text](image-8.png)

2. **Pie Chart:** A pie chart is a round graph that looks like a pie. It is divided into slices to show how big different parts of a whole group are. Each slice represents a part, and the size of the slice shows how large that part is compared to the others.
   **python code**
   ```python
   titanic['embarked'].value_counts().plot(kind='pie', autopct='%.2f')
   ```
   *Observation: According to this pie char, approx 73% people take their ship in southen region* <br>
   ![alt text](image-9.png)

   **python code**
   ```python
   titanic['pclass'].value_counts().plot(kind='pie', autopct='%.2f')
   ```
   *Observation: According to the pie char, 55% of people travel in 3rd class 24% of people travel from 1st class and only 20% of people are travel to 2nd class.* <br>
   ![alt text](image-10.png)

3. **count:** The number of non-null observations
   ```python
   count = pclass_data.count()
   ```

4. **Nunique**: The number of unique values
   ```python 
   nunique = pclass_data.nunique()
   ```

5. **Unique**: The unique values
   ```python
   unique = pclass_data.unique()
   ```

6. **Mode**: The most frequent value
   ```python
   mode = pclass_data.mode()[0]
   ```

7. **Value_counts:** The frequency of each unique value
   ```python
   value_counts = pclass_data.value_counts()
   ```
   ![alt text](image-11.png)

8. **Chi-Square Test - Goodness of fit**
   ![alt text](image-12.png)

   ## **Example 1:** Chi-Square Test for Goodness of Fit using Blood types
   - **Explanation**: This test checks if the observed frequencies of categorical data match an expected distribution.
   - **Example**: Suppose you want to test if the observed distribution of blood types in a population matches the expected distribution (e.g., 40% type A, 30% type B, 20% type O, 10% type AB).

   **Python code**
   ```python
   import scipy.stats as stats

   # Observed frequencies of blood types
   observed = [110, 85, 65, 40]

   # Expected frequencies based on the population distribution
   expected = [0.4 * sum(observed), 0.3 * sum(observed), 0.2 * sum(observed), 0.1 * sum(observed)]

   # Perform Chi-Square Test
   chi2, p = stats.chisquare(observed, expected)

   print(f"Chi-Square Statistic: {chi2}")
   print(f"P-value: {p}")
   ```
   ![alt text](image-13.png)

   **Output:**
   - Chi-Square Statistic: 4.86
   - P-value: 0.182

   **Explanation:**
   1. Chi-Square Statistic (4.86):
      * Measures the difference between observed and expected frequencies.
      * Larger values indicate a greater difference.
   
   2. P-value (0.182):
      * Represents the probability of observing the given chi-square statistic under the null hypothesis.
      * A high p-value (0.182) suggests that the difference is not statistically significant.

   **Conclusion:**
      * The observed frequencies are not significantly different from the expected frequencies.
      * We fail to reject the null hypothesis (observed matches expected).

   ## **Example 2:** Chi-Square Test for Goodness of Fit using Titanic Dataset

   This example demonstrates how to perform a Chi-Square Test for Goodness of Fit using the 'pclass' column from the Titanic dataset.

   **Python Code**

   ```python
   import pandas as pd
   from scipy.stats import chisquare

   # Load the Titanic dataset
   titanic = pd.read_csv('titanic.csv')

   # Observed frequencies of 'pclass'
   observed = titanic['pclass'].value_counts().sort_index()

   # Expected frequencies (assuming equal distribution)
   expected = [len(titanic) / 3] * 3

   # Perform Chi-Square Test
   chi2, p_value = chisquare(observed, expected)

   print(f"Chi-Square Statistic: {chi2}")
   print(f"P-value: {p_value}")
   ```
   ![alt text](image-14.png)

   **Output:**
   - Chi-Square Statistic: 191.8047138047138
   - P-value: 2.2394202231028854e-42

   **Explanation**
   1. Chi-Square Statistic (191.80):
      * This value measures the difference between the observed frequencies of passenger classes ('pclass') and the expected frequencies assuming an equal distribution.
      * A larger chi-square statistic indicates a greater difference between observed and expected frequencies.
   
   2. P-value (2.24e-42):
      * The p-value represents the probability of observing such a large difference between observed and expected frequencies if the null hypothesis (equal distribution) were true.
      * A very small p-value (close to zero) suggests strong evidence against the null hypothesis.

   **Conclusion**
      * The chi-square statistic is very large (191.80), indicating a significant difference between the observed and expected frequencies.
      * The p-value is extremely small (2.24e-42), providing strong evidence that the observed distribution of passenger classes is not equal.
      * Therefore, we reject the null hypothesis and conclude that the distribution of passenger classes ('pclass') in the Titanic dataset is not equally distributed.

# 2. Numerical Data
`Numerical data has continues value like age, salary etc. we can find the mean, median, min value, max value etc`

1. **Histogram:** In numerical data we have some range, we create a bins in that data. lets say we have age column in which it ranges from 0 to 80, we can create a bin size of 10 and create 8 bins. and count the how many passanger in each bins and we plot it.
   * histrogram also help us to understand the distribution of the data.
   * The whole idea behind the histogram is to understand the distribution of the data in that numerical columns.

   **Python code**
   ```python
   import matplotlib.pyplot as plt

   # Plot the histogram
   plt.figure(figsize=(10, 6))
   plt.hist(titanic['age'], bins=30, edgecolor='black')
   plt.title('Age Distribution of Titanic Passengers')
   plt.xlabel('Age')
   plt.ylabel('Frequency')
   plt.grid(True)
   plt.show()
   ```

   *Observation: According to the figure there are very less people below the age 15 and greater then age 50, majority of the people have age between 18 to 45 are traveling in the ship*
   ![alt text](image-15.png)

2. **Distplot:** The improvement of histogram we called it distplot. it also tell us the data distribution we called it PDF(probability density function). in the `y-axis` it has probabilty and in the x-axis it has `age` column.

   **Python Code**
   ```python
   # Set the style of the visualization
   sns.set(style="whitegrid")

   # Plot the distribution of the 'Age' column
   plt.figure(figsize=(10, 6))
   sns.distplot(titanic['age'], kde=True, bins=30)
   plt.title('Age Distribution of Titanic Passengers')
   plt.xlabel('Age')
   plt.ylabel('Frequency')
   plt.show()
   ```
   *Observation: using this graph we can easly find out what is the probability of having age=40 which comes to be 1.5%, it is good way to find out the probability by looking at he y-axis. similary for age 60 there is 0.5% probabiltly that is why this is called pdf.*
   ![alt text](image-17.png)

3. **Boxplot:** Thired type of plot when we dealing with numerical data is called box plot. it gives us 5-number summery. we generally use it when data has outliers.
   ![alt text](image-20.png)
   1. **Median(50th percentile):**: when we short the numerical value the middle number is called median.
   2. **Q1(25th percentile):** it show that 25 percentage of people are below certain range. for example cat test score 25 percenitle which mean 25% of people are below of you.
   3. **Q3(75th percentile):** it shows that 75 percentile value is less then current marking.
   4. **Minimum Value:** This is not the minimum value of the columns, it is `Q1-1.5 x IQR`.
   where `IQR = Q3-Q1`
   5. **Maximum Value:** `Q3 + 1.5 x IQR`

   `Note: if any value are less then calculated minimum or calculated maximum then that value is potential outliers.` <br>
   `This is avantage of 5-number summary, we can easly find out the potential outliers and eliminate as well.` <br>
   `When ever you are working with any noise data then you can plot a boxplot and check how much data is noise and how much data is outliers.`

   **Python code**
   ```python
   # Extract the 'Fare' column
   fares = titanic['fare']

   # Create a box plot
   plt.figure(figsize=(10, 6))
   plt.boxplot(fares, vert=False, patch_artist=True, boxprops=dict(facecolor='lightblue'))

   # Add titles and labels
   plt.title('Fare Distribution of Titanic Passengers')
   plt.xlabel('Fare')

   # Show the plot
   plt.show()
   ```
   ![alt text](image-21.png)

   **python code**
   ```python
   # Set the style of the visualization
   sns.set(style="whitegrid")

   # Create the box plot
   plt.figure(figsize=(10, 6))
   sns.boxplot(x=titanic['fare'], color='lightblue')

   # Add titles and labels
   plt.title('Fare Distribution of Titanic Passengers')
   plt.xlabel('Fare')

   # Show the plot
   plt.show()
   ```
   ![alt text](image-22.png)

   **Python code**
   ```python
   plt.figure(figsize=(10, 6))
   sns.boxplot(x=titanic['age'], color='lightblue')
   ```
   *Observation: Minimum value around 28 calculated maximum around 65 and beyound this value boxplot consider as potential outliers. if you wish you can eliminiated this outliers.*
   ![alt text](image-23.png)

4. **Minimum Value:**
   ```python
   titanic['age'].min()
   ```

5. **Maximum Value:**
   ```python
   titanic['age'].max()
   ```

6. **Mean:**
   ```python
   titanic['age'].mean()
   ```

7. **Standard deviation:**
   *example: calculate the stardard deviation of mens and women hair. men have very low standard deviation where as female has high standard deviations. this tells that most of the guys have standard deviation close to mean then girls.*

   Finding the standard deviation of the Age column (or any numerical data) in the Titanic dataset (or any dataset) serves several important purposes in data analysis and statistical interpretation:

   a. **Measure of Dispersion:** <br>
   The standard deviation (std) is a measure of the amount of variation or dispersion in a set of values. In this context, it tells us how much the ages of passengers on the Titanic vary from the average age (mean age). A higher standard deviation indicates that the ages are spread out over a wider range, whereas a lower standard deviation indicates that the ages are closer to the mean.
      ```python
      age_std = titanic_df['Age'].std()
      print(f'Standard Deviation of Age: {age_std}')
      ```
      *Observaton: Suppose the standard deviation of the Age column is 14.5. This indicates that the ages of the passengers tend to vary by about 14.5 years from the mean age.*

      ![alt text](image-24.png)

   b. **Data Understanding:**<br>
   Understanding the spread of ages among Titanic passengers can provide insights into the demographics of the passengers. For example, if the standard deviation is high, it suggests that the passengers were a diverse group in terms of age. This information can be crucial for various analyses, such as studying survival rates across different age groups.
      ```python
      age_std = titanic_df['Age'].std()
      print(f'Standard Deviation of Age: {age_std}')
      # Insight: High standard deviation indicates diverse age groups.
      ```
      *Observation: If the standard deviation of ages is high, such as 20 years, it suggests a wide range of ages among passengers.*
      ![alt text](image-24.png)


   c. **Statistical Analysis:**<br>
   The standard deviation is a fundamental concept in statistics and is used in various statistical formulas and tests. For instance, it plays a key role in hypothesis testing, confidence intervals, and in the calculation of z-scores, which are used to determine how far a particular data point is from the mean in units of standard deviations.

      * **Hypothesis Testing:** Suppose we want to test if the mean age of survivors differs significantly from the mean age of non-survivors.

      * The standard deviation is used in the calculation of the t-statistic, which helps determine if there is a statistically significant difference between the mean ages of survivors and non-survivors.
         ```python
         from scipy.stats import ttest_ind

         survivors = titanic_df[titanic_df['Survived'] == 1]['Age'].dropna()
         non_survivors = titanic_df[titanic_df['Survived'] == 0]['Age'].dropna()

         t_stat, p_value = ttest_ind(survivors, non_survivors)
         print(f'T-statistic: {t_stat}, P-value: {p_value}')
         ```

         ![alt text](image-25.png)

         **Explanation**:
         * T-statistic: -2.06668694625381
            - The T-statistic is a measure of the difference between the means of two groups (survivors and non-survivors), normalized by the variability of the samples.
            * A negative value indicates that the mean age of survivors is less than the mean age of non-survivors.
            * The magnitude of the T-statistic shows how much the means of the two groups differ relative to the variability in the data.
         
         * P-value: 0.03912465401348249
            - The P-value helps determine the statistical significance of the observed difference between the means of the two groups.
            - A P-value less than 0.05 (common significance level) suggests that the observed difference is statistically significant, meaning it's unlikely to have occurred by random chance.
            - In this case, the P-value is approximately 0.039, which is less than 0.05. This indicates that the difference in mean ages between survivors and non-survivors is statistically significant at the 5% significance level.


   d. **Normalization and Standardization:**<br>
   When preparing data for machine learning models, standard deviation is used in normalization and standardization processes. Standardization involves rescaling data to have a mean of 0 and a standard deviation of 1, which can improve the performance of certain algorithms.
      * **Standardization:** Rescaling the Age column to have a mean of 0 and a standard deviation of 1.

      * Standardizing the Age column helps in improving the performance of machine learning algorithms by ensuring each feature contributes equally to the result.
         ```python
         from sklearn.preprocessing import StandardScaler

         scaler = StandardScaler()
         titanic_df['Age_standardized'] = scaler.fit_transform(titanic_df[['Age']])
         print(titanic_df[['Age', 'Age_standardized']].head())
         ```


   **e. Comparative Analysis:**<br>
   By comparing the standard deviation of ages between different groups (e.g., different classes, survival status), we can identify patterns and differences. For instance, we might find that the standard deviation of ages is different between survivors and non-survivors, which could lead to further insights and hypotheses.
      * **Comparing Age Standard Deviation by Class:**
         ```python
         first_class_age_std = titanic_df[titanic_df['Pclass'] == 1]['Age'].std()
         second_class_age_std = titanic_df[titanic_df['Pclass'] == 2]['Age'].std()
         third_class_age_std = titanic_df[titanic_df['Pclass'] == 3]['Age'].std()

         print(f'First Class Age Std: {first_class_age_std}')
         print(f'Second Class Age Std: {second_class_age_std}')
         print(f'Third Class Age Std: {third_class_age_std}')
         ```

         *Observation: Suppose we find that the standard deviation of ages in first class is 10 years, second class is 15 years, and third class is 20 years. This indicates that the age range is most diverse in third class, potentially reflecting different demographics or family compositions across classes.*
         ![alt text](image-26.png)


8. **Variance:**
   ![alt text](image-27.png)

9. **Difference between Standard Deviation and variance**

9. **Independent two-sample t-test:**


---------------------------------------------------------------------------------------------------------
# Question & Answer
---------------------------------------------------------------------------------------------------------

#### Q1. 
