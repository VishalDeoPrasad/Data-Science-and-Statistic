# Statistics-and-Data-Analysis

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


