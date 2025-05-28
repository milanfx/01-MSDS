---
### 1. Least Squares Introduction 
---
> **1. Least Squares Method Overview**  
> - Goal: Estimate regression model parameters.
> - Assumption: Linear model form.
>   - e.g., Estimating intercept and slope(s) for predictors.
> - Applications: Model validation, explanation of relationships, and predictions.
> - Data Collection: Response and predictor data collection fixates these variables for analysis.

> **2. Simple Linear Regression**  
> - Definition: Regression with one response and one predictor variable.
> - Equation: $y_i = \beta_0 + \beta_1x_i + \epsilon_i$.
> - Estimation Goal: Find $\beta_0$ and $\beta_1$ that minimize squared vertical distances from data points to the regression line.
> - Best Fit Concept: The line that minimizes the sum of squared distances (errors) between observed data points and the line itself.
>   - e.g., Selection from many potential lines to identify the one that best represents the data trend.

> **3. Multiple Linear Regression Visualization**  
> - Complexity: Increases with more than one predictor; difficult to visualize beyond two dimensions.
> - Matrix Notation: $y = X\beta + \epsilon$ with $X$ as the design matrix and $\beta$ as the parameter vector.
> - Goal: Select $\beta$ to explain as much of $y$ without overfitting.
>   - e.g., For two predictors, visualize as selecting a plane in three-dimensional space that minimizes squared deviations.

> **4. Overdetermined Systems**  
> - Concept: More sample points than parameters, leading to a system without an exact solution.
> - Visual Representation: $y$ not lying within the column space of $X$ indicates no exact solution.
> - Least Squares Solution: An orthogonal projection of $y$ onto the column space of $X$, representing the best approximation.
---
### 2.  Least Squares Linear Algebra
---
> **1. Introduction to Linear Algebra for Least Squares**  
> - Objective: Understand linear algebra foundations for deriving the least square solution.  
> - Importance: Essential for efficiently calculating least squares in linear regression.

> **2. Basic Linear Algebra Concepts**  
> - Matrix and Vector Dimensions: $X$ is $m \times n$, $V$ is $n \times 1$, and $Y$ is $m \times 1$.
> - Matrix Transpose: Swapping rows and columns, changing $X$ from $m \times n$ to $n \times m$.
> - Symmetry of $X^TX$: $X^TX$ is symmetric, meaning $(X^TX)^T = X^TX$.

> **3. Derivatives in Linear Algebra**  
> - Derivative of $Y$ with respect to $V$: Results in the matrix $X$.
> - Derivative of $Y^T$ with respect to $V$: Yields $X^T$.
>   - e.g., Derivative process involves isolating constants in the linear equation system.

> **4. Quadratic Forms and Derivatives**  
> - Quadratic Form: $C = V^T(X^TX)V$ is a scalar.
> - Derivative of Quadratic Form: $\frac{dC}{dV} = 2X^TXV$.
> - Dimension Analysis: Ensures that matrix multiplication is properly defined and results in a scalar.
---
### 3. Least Squares Solution
---
> **1. Defining Key Terms for Least Squares**  
> - Residuals: $\epsilon_i hat$, difference between measured response and fitted line or surface.
> - Fitted Values: $y_i hat = \beta_0 hat + \beta_1 hat x_{i1} + ... + \beta_p hat x_{ip}$, estimators of the mean data or predictions for new $x$ values.
> - Hat Matrix: $H = X(X^TX)^{-1}X^T$, used for theoretical calculations in least squares.

> **2. Deriving the Least Square Solution**  
> - Objective: Minimize the sum of the squares of residuals (RSS).
> - Residual Sum of Squares: $RSS = (y - X\beta)^T(y - X\beta)$, represents the square of the 2-norm of the vector $y - X\beta$.
> - Simplification Process: Involves transposing and multiplying matrices to simplify the RSS formula.
> - Solution Derivation: Involves setting the derivative of RSS with respect to $\beta$ to zero and solving for $\beta$.
>   - e.g., $X^TX\beta = X^Ty$ leads to the least squares estimator $\beta hat = (X^TX)^{-1}X^Ty$.

> **3. Assumptions of Least Squares**  
> - Error Term Mean: Zero mean for every error term in the model.
> - Linearity: Expected value of the response is linear in parameters before data collection.
> - Covariance Between Error Terms: Zero for $i \neq j$, indicating no correlation between errors, and constant variance for $i = j$.
> - Existence of $(X^TX)^{-1}$: Necessary for solving the least squares equation.

> **4. Implementation and Assumptions**  
> - Least Squares in Practice: Implemented using numerical algorithms in software (e.g., R's lm function) rather than direct matrix inversion to avoid computational issues.
> - Importance of Assumptions: Violating least squares assumptions can lead to suboptimal solutions.
---
### 4. Regression Modeling in R 1
---
> **1. Data Overview**  
> - Dataset: Consists of 200 companies with advertising budgets for YouTube, Facebook, and newspapers.
> - Measurement: Budgets in thousands of dollars, sales in thousands of units.

> **2. Data Cleaning and Preliminary Checks**  
> - Missing Values: Checked for NAs and unusual codes (e.g., a string of nines).
> - Data Integrity: Ensured no missing values or incorrect coding in the dataset.
> - Summary Statistics: Reviewed for plausibility and identification of potential outliers.

> **3. Exploratory Data Analysis (EDA)**  
> - Univariate Analysis: Histograms for each variable to assess distribution shapes and identify outliers, especially in the newspaper budget.
> - Bivariate Analysis: Correlations and scatter plots to explore relationships between sales and advertising budgets.
>   - e.g., Correlation matrix visualized for pairwise relationships among variables.

> **4. Insights from EDA**  
> - Correlations: High correlation between sales and YouTube/Facebook budgets; lower correlation with newspaper budget.
> - Scatter Plot Observations:
>   - Sales and YouTube: Non-linear relationship with increasing variability at higher budget levels.
>   - Sales and Facebook: Potentially linear relationship but with significant variability that could suggest non-linearity.
>   - Sales and Newspaper: No apparent relationship, resembling random scatter.
> - Outliers: Identified in the newspaper advertising budget using box plots and the interquartile range (IQR) criterion.

> **5. Considerations for Regression Modeling**  
> - Sample Size: Limited data restricts the separation into exploratory, training, and testing sets, necessitating cautious interpretation of results.
> - Variable Distributions: Non-normal distributions observed, but regression analysis remains robust to these deviations.
> - Linear vs. Non-linear Relationships: Scatter plots suggest varying relationships between sales and advertising budgets, with potential non-linearity in some cases.
---
### 5. Least Squares Justification: Gauss-Markov Theorem and Maximum Likelihood Estimation
---
> **1. Justifications for Least Squares**  
> - Gauss-Markov Theorem: Least squares estimator is the best unbiased estimator under specific conditions.
> - Equivalence to Maximum Likelihood Estimator: Under normality assumption, least squares matches the maximum likelihood estimator, inheriting its beneficial properties.

> **2. Gauss-Markov Theorem**  
> - Conditions: Zero mean errors, linear expectation for responses, uncorrelated errors with constant variance, and existence of $(X^TX)^{-1}$.
> - Implication: Among unbiased estimators of $\beta$, least squares has the lowest variance.

> **3. Balance of Bias and Variance**  
> - Least squares estimator is unbiased: Expectation equals the true parameter values.
> - Importance of Low Variance: Reduces variability of estimator across different samples.

> **4. Beyond Gauss-Markov**  
> - Regularization: Introduces bias to reduce variance in contexts where assumptions may be violated or in the presence of high-dimensional data.

> **5. Maximum Likelihood Estimation (MLE) Equivalence**  
> - Additional Assumption: Error terms are normally distributed.
> - MLE Properties: Asymptotically unbiased, efficient, and consistent.

> **6. Derivation of MLE**  
> - Log Likelihood Function: Derived from the joint probability density function of $y$, focusing on the part relevant to $\beta$.
> - Maximization: Maximizing the log likelihood is equivalent to minimizing the positive residual sum of squares, aligning with least squares.

> **7. Implications for Estimation**  
> - Least squares optimization mirrors MLE under normal error distribution, reinforcing its validity in statistical modeling.
> - Acknowledges potential for bias-variance trade-offs in estimator selection, with regularization as an example.
---
### 6. Sums of Squares and Estimating the Error Variance
---
> **1. Introduction to Sums of Squares in Linear Regression**  
> - Purpose: Define sums of squares for estimating error variance and understanding model performance.
> - Visualization: Demonstrated through deviations between actual data points, the sample mean ($y_{bar}$), and the regression line ($y_i hat$).

> **2. Deviations and Their Interpretations**  
> - $y_i$ to $y_{bar}$: Measures error using the simplest model, indicating total variability.
> - $y_i$ to $y_i hat$: Represents error using the regression model, reflecting unexplained variability.
> - $y_i hat$ to $y_{bar}$: Difference between regression model predictions and the sample mean, showing the improvement of regression over the mean model.

> **3. Sums of Squares Definitions**  
> - Residual Sum of Squares (RSS): Sum of squared deviations from the regression model, indicating unexplained variability.
> - Explained Sum of Squares (ESS): Measures improvement of regression model over the sample mean, quantifying explained variability.
> - Total Sum of Squares (TSS): Total variability in the data, akin to the sample variance without normalization.

> **4. Residual Sum of Squares (RSS) Insight**  
> - Interpretation: Low RSS suggests a model that closely fits the data, while high RSS indicates significant unexplained variability.
> - Visualization: Compared across three scenarios with varying degrees of data scatter around the regression line.

> **5. Estimating Error Variance ($\sigma^2$)**  
> - Formula: $\sigma_{hat}^2 = \frac{RSS}{n - p + 1}$, where $n$ is the sample size and $p$ is the number of predictors.
> - Degrees of Freedom: Explained as the adjustment for the number of parameters estimated in the model.

> **6. Properties of $\sigma_{hat}^2$**  
> - Unbiased Estimator: On average, yields the true error variance, $\sigma^2$.
> - Importance: Used in inferential procedures like confidence intervals and hypothesis testing for model parameters.
---
### 7. The Coefficient of Determination
---
> **1. Coefficient of Determination (R-Squared)**  
> - Definition: Measures the proportion of variability in the response variable explained by the regression model.
> - Calculation: $R^2 = 1 - \frac{RSS}{TSS}$, where RSS is the residual sum of squares and TSS is the total sum of squares.

> **2. Interpretation of R-Squared**  
> - Range: Between 0 and 1, with values close to 1 indicating a high proportion of variability explained by the model.
> - Contextual Use: Valid and useful when the model form is correct or approximately correct.

> **3. Misuses of R-Squared**  
> - Incorrect Model Fit: High R-squared does not guarantee the model is the correct fit for the data.
> - Natural Variability: Low R-squared can occur even with the correct model due to high natural variability in data.
> - Comparison of Models: R-squared should not be used to compare models with different numbers of predictors, as it always increases with additional predictors.
> - Causal Inference: R-squared does not imply causal relationships between variables.

> **4. Sums of Squares in Regression**  
> - Total Sum of Squares (TSS): Captures total variability around the sample mean ($y_{bar}$).
> - Residual Sum of Squares (RSS): Quantifies variability unexplained by the regression model.
> - Explained Sum of Squares (ESS): Measures variability explained by the regression model.

> **5. Adjusted R-Squared**  
> - Purpose: Adjusts R-squared to account for the number of predictors in the model, allowing for fairer model comparisons.
> - Calculation: Adjusts for the degrees of freedom associated with the number of predictors.

> **6. Limitations and Cautions**  
> - R-squared Value Misinterpretation: High or low R-squared values do not inherently indicate a good or bad model.
> - Model Complexity: Adding predictors always increases R-squared, which can mislead model evaluation.
> - Causality: High R-squared does not confirm causal relationships between predictors and the response variable.
> - Use in Data Science: Understanding the limitations of R-squared is crucial for accurate data analysis and interpretation.
---
### 8. The Problem of Non-identifiabiliity
---
> **1. Non-Identifiability in Linear Regression**  
> - Definition: A linear regression model is non-identifiable when there are infinitely many solutions to the normal equations, indicating infinitely many least squares solutions or maximum likelihood estimators.
> - Cause: Arises when the design matrix $X$ has linearly dependent columns, preventing $X^TX$ from being invertible.

> **2. Linear Dependence in Design Matrix**  
> - Linearly Dependent Columns: Occurs when one column in $X$ can be written as a linear combination of other columns.
> - Example: Including predictor variables measured in different units (e.g., height in centimeters and inches) that are constant multiples of each other.

> **3. Resolving Non-Identifiability**  
> - Elimination of Redundant Predictors: Removing columns that are constant multiples of others to ensure a unique solution for the model.
> - Decision Criteria: Choice of which variable to drop may depend on the modeling goal, such as causal explanation or prediction accuracy.

> **4. Near Non-Identifiability: Multicollinearity**  
> - Definition: Occurs when predictor variables are highly correlated but not exactly linearly dependent, complicating model estimation.
> - Impact: Makes it difficult to determine the contribution of individual predictors to the response and to find a stable solution.
> - Future Discussion: Strategies for addressing multicollinearity and its implications on model interpretation will be explored in subsequent lessons.
---
### 9. Regression Modeling in R 2
---
> **1. Non-Identifiability and Linear Dependence**  
> - Non-Identifiability: Occurs when $X^TX$ cannot be inverted, leading to infinitely many solutions.
> - Linear Dependence: When columns of the design matrix $X$ are linearly dependent, making $X^TX$ non-invertible.

> **2. Causes of Non-Identifiability**  
> - Predictors as Constant Multiples: One predictor is a constant multiple of another, e.g., measuring the same variable in different units.

> **3. Resolving Non-Identifiability**  
> - Elimination of Redundant Variables: Removing predictors that are constant multiples of others to achieve a unique solution.
> - Consideration for Model Goals: Decision to drop variables should be guided by whether the model's aim is explanation or prediction.

> **4. Non-Identifiability in R**  
> - R Handling: R automatically drops columns causing non-identifiability, resulting in NA values for associated coefficients.

> **5. Multicollinearity: Near Non-Identifiability**  
> - Definition: Occurs when predictors are highly correlated but not exactly linearly dependent.
> - Detection Challenge: Unlike exact linear dependence, multicollinearity can be less apparent and not directly result in NA coefficient values.

> **6. Simulating Collinear Data**  
> - Simulation Approach: Creating a predictor ($x_3$) highly correlated with another ($x_1$) to illustrate multicollinearity effects.
> - Model Misestimation: Multicollinearity can lead to misleading parameter estimates, such as a negative estimate for a positively related predictor.

> **7. Diagnosing Multicollinearity**  
> - Sign Change Indicator: A change in the sign of an estimated coefficient compared to its expected value can indicate multicollinearity.
> - Further Measures: Introduction to additional diagnostics and remedies for multicollinearity to be discussed in future lessons.
---