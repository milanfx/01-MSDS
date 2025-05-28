---
### 1. Linear Regression Statistical Inference
---
> **1. Importance of Statistical Inference in Linear Regression**  
> - Context: Statistical inference critical for understanding linear regression outcomes.  
> - Data: Analysis based on marketing data with four variables over 200 units.  
>   - e.g., Variables include YouTube, Facebook, newspaper budgets (in thousands of dollars) and sales (in thousands of units).  
> - Focus: Estimated coefficient for newspaper advertising budget.  
>   - e.g., A $1,000 increase in newspaper budget is associated with a decrease in sales by approximately one unit, adjusting for other budgets.  

> **2. Statistical Significance**  
> - Definition: Assesses if a parameter differs statistically from zero.  
> - Importance: Determines if observed effects are due to chance or reflect actual trends.  
> - Application: Questions the negative impact of newspaper budget on sales.  
>   - e.g., Is the negative association a real trend or noise in the data?

> **3. Practical Significance**  
> - Definition: Concerns the real-world importance or relevance of statistical findings.  
> - Evaluation: Considers the impact of a $1,000 increase in newspaper budget on sales.  
> - Business Perspective: Analyzes the advisability of newspaper advertising investment based on its slight negative return.  

> **4. Least Squares Estimation**  
> - Sensitivity: Values obtained are sensitive to the sample data used.  
> - Variability: Different samples yield different estimates.  
> - Unbiasedness: On average, least squares estimator accurately estimates true values.  
> - Variance: Variability in estimates depends on fixed predictor values and variance term $\sigma^2$.  
>   - e.g., High $\sigma^2$ leads to greater variability in least squares estimates.  
> - Sample Size: Increasing sample size improves estimator precision.  
---
### 2. The Sampling Distribution of the Least Squares Estimator
---
> **1. Sampling Distribution of Least Squares Estimator**  
> - Concept: Sampling distribution defines the probability distribution of the least squares estimator across all random samples.  
> - Importance: Essential for statistical inference in regression analysis, enabling hypothesis tests and confidence interval construction.  

> **2. Statistical Inference in Regression**  
> - Hypothesis Testing: Determines if a slope parameter significantly differs from zero.  
> - Confidence Intervals: Quantifies uncertainties around regression parameters.  
>   - e.g., Requires knowledge of the sampling distribution and standard error.  

> **3. Assumptions for Least Squares Estimation**  
> - Structural Form: Assumes error terms are zero mean and response expectation fits the linear model.  
> - Constant Variance and Independence: Error terms have constant variance and are independent.  
> - Covariance: Covariance between error terms is zero, indicating independent errors.  
> - Matrix Invertibility: $X^TX$ inverse exists for solving least squares estimator.  

> **4. Normality Assumption for Inference**  
> - Normal Distribution: Adds normality assumption for the distribution of response variables.  
> - Robustness: Coverage properties of confidence intervals and hypothesis test error rates are relatively robust to deviations from normality.  

> **5. Sampling Distribution Characteristics**  
> - Formulation: Least squares estimator as a linear combination of normally distributed variables.  
> - Distribution: The least squares estimator follows a normal distribution.  
> - Unbiasedness: The estimator is unbiased, meaning its expected value equals the true parameter value.  
> - Variance-Covariance Matrix: Defined by $\sigma^2(X^TX)^{-1}$, affecting the precision of the estimator.  

> **6. Variance of Least Squares Estimator**  
> - Components: The variance-covariance matrix is pivotal for understanding estimator variability.  
> - Diagonal Terms: Represent variance for each component of the estimator.  
> - Off-Diagonal Terms: Indicate covariance between estimator components.  
>   - e.g., Symmetric due to interchangeable covariance terms.  

> **7. Derivation of Estimator Properties**  
> - Expectation: Proves the least squares estimator's expectation equals the true parameter vector.  
> - Variance Derivation: Demonstrates how to derive the variance-covariance matrix of the estimator.  
> - Simple Linear Regression: Analysis of variance for intercept and slope terms in simple regression.  
>   - e.g., Variance influenced by sample size, variability in response data, and design points.  
---
### 3. T-Tests for Individual Regression Parameters
---
> **1. Hypothesis Testing for Regression Parameters**  
> - Objective: Test if a regression parameter equals a constant, typically zero.  
> - Hypothesis: Null hypothesis posits no correlation between predictor and response.  
> - Significance Level: Alpha defines the probability of a type I error, often set at 5%.  

> **2. Test Statistic Formulation**  
> - General Form: Test statistic as $(\theta_{hat} - \Theta_0) / SE(\theta_{hat})$.  
> - Regression Context: Uses least squares estimator minus hypothesized value over its standard error.  
>   - e.g., For $\beta_j$, it's $(\beta_{j_{hat}} - c) / SE(\beta_{j_{hat}})$.  

> **3. Standard Error of Beta Hat**  
> - Variance-Covariance Matrix: $\sigma^2(X^TX)^{-1}$ provides variances for estimators.  
> - Standard Error: Square root of the variance of $\beta_{j_{hat}}$, adjusted for estimation of $\sigma$.  
>   - e.g., $\sigma_{hat}$ derived from residual sum of squares divided by degrees of freedom.  

> **4. T-Distribution of Test Statistic**  
> - Distribution: Assumes a t-distribution due to normality of response and unknown $\sigma$.  
> - Degrees of Freedom: $n - p - 1$, where $n$ is sample size and $p$ is number of parameters.  

> **5. Application in R**  
> - Estimation: Demonstrates calculation of least squares estimates, standard errors, and t-values in R.  
> - P-Value: Derived from t-distribution, indicating whether to reject the null hypothesis.  
>   - e.g., Rejecting null hypothesis suggests parameter significantly differs from zero.  
> - Practical Significance: Distinguishes between statistical significance and practical/business relevance.  
>   - e.g., Decision on marketing budget allocation based on p-values and effect sizes.  
---
### 4. T-Tests in R
---
> **1. Dataset Overview**  
> - Dataset: 325 books with prices and characteristics like weight, pages, and cover type.  
> - Exploration: Understanding basic trends and identifying missing values.  

> **2. Handling Missing Data**  
> - Deletion: Removing rows or columns with missing values, considering randomness of missing data.  
> - Imputation: Replacing missing values with estimates, such as the mean for each variable.  
>   - e.g., Replacing NA in list price with the mean list price.  

> **3. Data Analysis Complications**  
> - Outliers: Identifying and understanding the impact of outliers on analysis.  
> - Influential Points: Recognizing points that significantly affect the linear model fit.  
>   - e.g., A book with an imputed list price creating a misleading trend.  

> **4. Linear Model Analysis**  
> - Model: Linear regression with Amazon price as response and list price, pages, and width as predictors.  
> - Multicollinearity: Checking correlations between predictors to avoid correlated predictors.  

> **5. Hypothesis Testing with Linear Models**  
> - Alpha Setting: Pre-specifying a significance level, typically at 5%, for hypothesis tests.  
> - P-Values: Interpreting p-values for each predictor to assess statistical significance.  

> **6. Practical Significance vs. Statistical Significance**  
> - Example: Assessing the significance of the number of pages predictor based on its p-value and effect size.  
> - Practicality: Considering the effort and precision needed for data collection versus the predictive power of a variable.  
---
### 5. Multiple Statistical Comparisons - F-Test
---
> **1. Multiple Comparisons Problem**  
> - Issue: Multiple comparisons can lead to false positive results.
> - Example: A 2015 study reported weight loss in individuals eating dark chocolate daily, which was a false positive.
>   - e.g., The study found a 10% faster weight loss in the chocolate group, widely reported but later identified as false.

> **2. False Positive Calculation**  
> - Calculation: Method to calculate the probability of finding a false positive.
> - Formula: $1 - (1 - \alpha)^n$ where $\alpha$ is the significance level and $n$ is the number of tests.
>   - e.g., With 18 variables tested and $\alpha = 0.05$, the chance of at least one false positive is about 60%.

> **3. Regression and Type I Error**  
> - Context: In regression analysis, multiple t-tests increase the chance of Type I error.
> - Type I Error: Occurs when a predictor not associated with the response is incorrectly kept in the model.
> - Solution: Use of F-test to control the overall Type I error rate.

> **4. Simulation Example**  
> - Setup: 51 variables generated from a normal distribution with no inter-relationships, used in a linear regression model.
> - Outcome: Several predictors appeared significant due to chance, illustrating the problem of multiple comparisons.
>   - e.g., Variables V3, V8, V14, V17, V35, and V49 showed p-values less than 0.05 by chance.
---
### 6. The F-Test
---
> **1. Introduction to F Test**  
> - Concept: The F test is used to control the overall Type I error rate in multiple comparisons, especially in linear regression.
> - Background: Requires understanding of the F distribution, which depends on the Chi Square distribution.

> **2. Chi Square Distribution**  
> - Definition: A Chi Square distribution is a special case of the gamma distribution with shape parameter $\frac{n}{2}$ and scale parameter $\frac{1}{2}$.
> - Application: Arises when summing the squares of standard normal random variables or when calculating the sum of squared deviations in statistics.

> **3. F Distribution**  
> - Definition: An F distribution arises from the ratio of two Chi Square distributions divided by their degrees of freedom.
> - Formula: $X = \frac{X_1 / D_1}{X_2 / D_2}$ where $X_1$ and $X_2$ are Chi Square distributed and $D_1$, $D_2$ are their degrees of freedom.

> **4. Utilizing the F Distribution**  
> - Full Model vs. Reduced Model: The F test compares a full regression model (all predictors considered) against a reduced model (subset of predictors) to control Type I error rate.
> - Test Statistic: The test statistic for the F test involves the residual sum of squares from both models and their degrees of freedom.

> **5. Conducting the F Test**  
> - Hypothesis Testing: Tests if the reduced model is sufficient to explain variability in the data against the alternative that the full model is necessary.
> - Calculation: The F statistic is calculated using the difference in residual sum of squares between the reduced and full model, divided by their respective degrees of freedom.

> **6. Full F Test**  
> - Special Case: Considers a reduced model with no predictors, testing if at least one predictor is needed to explain variability in the response.
> - Application: Helps identify if any predictors significantly contribute to the model, controlling for the inflated Type I error from multiple comparisons.

> **7. Practical Example**  
> - Scenario: A dataset with variables generated randomly demonstrates the significance of using the F test over individual T tests to avoid Type I errors.
> - Result: The full F test indicated no predictors were needed, contrasting with individual T tests that suggested significant predictors due to Type I errors.
---
### 7. The F-Test in R
---
> **1. Introduction to F-tests in R**  
> - Objective: Learn to perform full and partial F-tests using R.
> - Dataset: Amazon book data with variables such as list price, Amazon price, book dimensions, and type.

> **2. Preparing the Data**  
> - Cleaning: Ensure data matches previous t-test models.
> - Alpha: Set significance level at $0.05$.

> **3. Defining the Full Model**  
> - Model: Includes list price, pages, and width as predictors with Amazon price as the response.

> **4. Full F-test**  
> - Output: Obtained from summary of linear model in R, includes F-statistic, degrees of freedom, and p-value.
> - Hypothesis: Tests if any predictors are necessary, with a low p-value indicating the need for at least one predictor.

> **5. Significance of Full F-test**  
> - Guidance: Perform before individual t-tests. A non-significant full F-test suggests no predictors are needed.

> **6. Partial F-test Setup**  
> - Scenario: Considering models with subsets of predictors to determine necessity beyond the null model.
> - Method: Use ANOVA function in R with reduced and full model as arguments.

> **7. ANOVA Table Insights**  
> - Provides: Residual degrees of freedom, residual sum of squares, F statistic, and p-value.
> - Conclusion: A small p-value indicates the reduced model is insufficient, guiding towards a more comprehensive model.

> **8. Final Model Consideration**  
> - Decision: Based on statistical and practical significance of predictors, possibly excluding non-significant ones.
> - Example Model: $Y = intercept + (parameter \times list\ price) + (parameter \times pages)$.

> **9. Comparing Models with One Predictor Difference**  
> - Consistency: F-test and t-test results should align when comparing models differing by only one predictor.
> - Relationship: T and F distributions are related; squaring a T-distributed variable yields an F-distributed variable.
---
### 8. Confidence Intervals in the Regression Context
---
> **1. Confidence Intervals for Regression Parameters**  
> - Distribution: Least squares estimator is normally distributed with mean equal to $\beta$ and covariance $\sigma^2(X^TX)^{-1}$.
> - CI Formula: $\beta_j \hat{} \pm t_{\alpha/2, n-p+1} \times SE(\beta_j \hat{})$, where $SE$ is the standard error of $\beta_j \hat{}$.
>   - e.g., $SE(\beta_j \hat{}) = \sqrt{\hat{\sigma}^2 \times (X^TX)^{-1}_{jj}}$, $jj$ being the diagonal.

> **2. R Shortcut for Confidence Intervals**  
> - Function: `confint(lm_object)` provides CIs for all model parameters at 95% by default.
> - Customization: `confint(lm_object, level = custom_level)` to adjust confidence level.

> **3. Confidence Intervals for Mean Response**  
> - Objective: Estimate the mean value of the response for a new set of predictors $X^*$.
> - Point Estimate: $Y \hat{} = X^* \beta \hat{}$ for new predictor values.
> - Interval Estimate: Requires calculating $SE(Y \hat{})$ which involves $X^*$, the new predictor values, and the variance of $\beta \hat{}$.

> **4. Variance of Mean Response Estimate**  
> - Formula: $Var(X^* \beta \hat{}) = X^* \sigma^2 (X^TX)^{-1} X^{*T}$, leading to the confidence interval calculation for $Y \hat{}$.
> - CI for Mean Response: $Y \hat{} \pm t_{\alpha/2, n-p+1} \times SE(Y \hat{})$ where $SE(Y \hat{}) = \sqrt{\hat{\sigma}^2 X^* (X^TX)^{-1} X^{*T}}$.

> **5. Predict Function in R**  
> - Usage: `predict(lm_object, newdata = new_predictor_dataframe, interval = "confidence", level = custom_level)` for CIs of mean response at new predictor values.
> - Note: `newdata` argument is crucial for specifying the new set of predictors $X^*$.
---