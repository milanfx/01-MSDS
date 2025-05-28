---
### 1. Model Selection Methods
---
> **1. Need for Model Selection Methods**  
> - Motivation: Address the challenge of selecting a regression model without strong theoretical guidance.
> - Theory reliance: Physics and biology often have theories dictating variable relationships, less so in social sciences.
> - Model selection goal: Choose a model that best explains data and predicts outcomes, avoiding underfitting and overfitting.

> **2. Problems of Extremes in Model Selection**  
> - Underfitting: Models too small, failing to capture systematic variability.
> - Overfitting: Models too large, mistaking random variability for systematic.
> - Balance: Seek a model that avoids both underfitting and overfitting.

> **3. Limitations of R Squared for Model Selection**  
> - R Squared increase: Adding predictors always increases R squared, leading to potential overfitting.
> - Least squares: Additional predictors reduce residual sum of squares, artificially inflating R squared.

> **4. Challenges with T-tests and F-tests in Large Model Spaces**  
> - F-tests limitation: Not practical for comparing many models with a large number of predictors.
> - Model space complexity: Enormous combinations of predictors, including functions and interactions, exceed the utility of simple tests.

> **5. Strategies for Navigating Model Space**  
> - Hierarchical structure: Follows rules for adding or removing terms based on their order.
> - Theoretical guidance: Leverage existing theories to reduce possible model space and guide selection.

> **6. Methods for Model Selection**  
> - Hypothesis testing methods: Include backward elimination, forward selection, and step-wise regression, though with limitations.
> - Criterion-based methods: Seek balance between fitting well and avoiding overly complex models, employing criteria like AIC, BIC, and adjusted R squared.
---
### 2. Testing-Based Procedures
---
> **1. Testing Based Procedures for Model Selection**  
> - Introduction: Explore hypothesis tests like F and T tests for model selection.
> - Methods: Include backward elimination, forward selection, and stepwise regression.
> - Issues: Lack of statistical justification and potential for missing optimal model.

> **2. Backward Elimination**  
> - Process: Start with full model, iteratively remove predictors with highest p-value above a threshold.
> - Iteration: Continue until all predictors have p-values below the threshold.

> **3. Forward Selection**  
> - Starting point: Begin with all possible simple linear regression models for each predictor.
> - Selection: Choose model with lowest p-value, then add predictors iteratively based on lowest p-value for new predictor.
> - Threshold: Continue until no additional predictors have p-value below a set threshold.

> **4. Stepwise Regression Variations**  
> - Bidirectional stepwise regression: Allows adding or removing variables at each iteration.
> - R function support: Use of `update` function in R for implementing selection methods.

> **5. Limitations and Cautions**  
> - Lack of statistical justification: No robust basis for using testing based procedures.
> - Potential for missing optimal model: Sequential addition or removal may overlook the best model.
> - Inflation of type 1 error: Multiple testing overstates the importance of remaining predictors.
> - Misalignment with regression goals: Procedures do not necessarily select causally relevant or predictive variables.
> - Tendency towards smaller models: May exclude predictors valuable for prediction.

> **6. Usage in R**  
> - Practical walkthrough: Demonstration of backward elimination and forward selection using R's `lm` and `update` functions.
> - Caution advised: Emphasis on understanding limitations and moving towards more justified model selection methods.
---
### 3. Criterion-Based Procedures: AIC
---
> **1. Criterion-Based Model Selection Procedures**  
> - Introduction: Explore alternatives to test-based procedures, starting with Akaike Information Criterion (AIC).
> - AIC focus: Used for model selection by comparing models based on a specific criterion.

> **2. Concept of True Function and Model Approximation**  
> - True function: Theoretical model that generated the data, unknown in statistical modeling.
> - Model attempts: Various models (g1, g2, g3, etc.) constructed to estimate the true function.

> **3. Distance Metric for Model Selection**  
> - Kullback-Leibler distance: Measures the distance between the true function and estimated models.
> - Distance attributes: Non-negative, zero only when the estimated model equals the true function.

> **4. Estimating Distance for AIC**  
> - Rewriting distance: Incorporate least squares or maximum likelihood estimator for parameters.
> - Model comparison: Simplify by dropping constants irrelevant to comparing different models (g).

> **5. AIC Formulation**  
> - AIC equation: Derived from estimating the significant part of the distance metric.
> - Components: Involves the number of predictors (p) and the negative log likelihood evaluated at the maximum likelihood estimator (MLE).

> **6. AIC Application to Linear Regression**  
> - Linear regression AIC: Specific case where AIC is applied to evaluate linear regression models.
> - Calculation: Involves the number of predictors and the log of the residual sum of squares divided by the number of observations (n).

> **7. Balancing Fit and Model Complexity**  
> - Objective: Seek models with good fit (low residual sum of squares) but penalize for increasing number of predictors.
> - Principle: Only add parameters that significantly improve model fit.

> **8. Choosing Models with AIC**  
> - Model selection: Opt for the model that minimizes the AIC value.
> - AIC values plot: Illustrates how AIC varies with the number of predictors, aiding in selecting the optimal model.

> **9. Implementing AIC in R**  
> - Future lesson: Detailed guidance on calculating AIC for models in R and plotting AIC values to facilitate model selection.
---
### 4. Criterion-Based Procedures: BIC
---
> **1. Introduction to Bayes Information Criterion (BIC)**  
> - BIC derivation: Utilizes Bayesian methodology, contrasting with frequentist methods like maximum likelihood estimation.
> - Comparison with AIC: Similar to AIC but includes a different penalty term for the number of parameters.

> **2. BIC Formula and Interpretation**  
> - BIC equation: \(p + 1\) (number of parameters) \(\times \log(n)\) (sample size) \(- 2 \times\) log-likelihood evaluated at MLE.
> - Penalty term: BIC imposes a higher penalty for adding parameters compared to AIC, favoring simpler models.

> **3. AIC vs. BIC for Model Selection**  
> - Model fit vs. complexity: Both AIC and BIC balance model fit and complexity but penalize additional parameters differently.
> - Appropriate usage: AIC is preferred for prediction tasks, while BIC is argued to be better for explanatory models seeking to identify the true generating process.

> **4. The True Model and Candidate Models**  
> - Asymptotic properties: BIC is said to select the true model with probability 1 as sample size \(n\) goes to infinity, a property not guaranteed by AIC.
> - Practical considerations: The true model is rarely among the set of candidate models, challenging the practical applicability of BIC's asymptotic advantage.

> **5. Causality and Model Selection**  
> - Limitations of statistical procedures: Neither BIC nor any criterion-based model selection method directly addresses causality, which is essential for explanatory modeling.
> - Reliance on theory or experiments: Establishing causal relationships requires theoretical frameworks or experimental designs beyond statistical correlations.
---
### 5. Criterion-Based Procedures: Adjusted R-Squared
---
> **1. Introduction to Adjusted R Squared**  
> - Purpose: Introduces adjusted R squared as a criterion for model selection, accommodating model complexity.

> **2. Comparison of Full and Reduced Models**  
> - Full model: Contains all considered predictors.
> - Reduced model: Excludes one or more predictors.
> - Residual sum of squares: Always smaller for the full model compared to the reduced model.

> **3. Limitations of Residual Sum of Squares and R Squared**  
> - Inadequacy for comparison: Direct comparison using these metrics is biased towards models with more predictors.
> - R squared increase: Adding predictors always increases R squared, not indicating a true improvement in model fit.

> **4. Adjusted R Squared Formula**  
> - Definition: Adjusts R squared for the number of predictors, making it suitable for comparing models of different sizes.
> - Formula: Adjusted R squared takes into account the degrees of freedom associated with the residual and total sum of squares.

> **5. Impact of Adding Predictors**  
> - Model complexity: Adding predictors increases the complexity, affecting the adjusted R squared.
> - Balance of fit and complexity: Adjusted R squared increases only if the addition of predictors significantly improves model fit.

> **6. Using Adjusted R Squared for Model Selection**  
> - Selection criterion: Opt for the model with the highest adjusted R squared, indicating an optimal balance between fit and complexity.
---
### 6. Criterion-Based Procedures: Mean Squared Prediction Error
---
> **1. Mean Squared Prediction Error for Model Selection**  
> - Importance: Mean squared prediction error aids in model selection.
> - Predictive Model: Statistical model providing prediction intervals based on predictors not used in training.
> - Regression Models: Utilized for prediction with a formula y hat = X * Beta hat for new values y star at X star.
>   - e.g., Fitted value computation using X star matrix for prediction.
> - Mean Squared Prediction Error Calculation: Involves extracting relevant rows from X star matrix and computing the error by comparing true values and predicted values.
>   - e.g., y_i star hat as the point prediction from row vector times Beta hat.
> - Deviation Analysis: Focuses on the average distance between true values and predicted values to assess prediction accuracy.
>   - e.g., Squaring deviations and averaging them to determine mean squared prediction error.
> - Model Comparison: Utilizes mean squared prediction error to compare models by splitting data into training and test sets, fitting models on training data, and evaluating on test data.
>   - e.g., Choosing the model with the lowest mean squared prediction error for prediction efficacy.

> **2. Model Evaluation and Selection Process**  
> - Data Splitting: Dividing data into training and test sets, commonly with an 80-20 ratio.
> - Model Fitting: Applying several competing models to the training set to establish predictions.
> - Error Calculation: Determining mean squared prediction error for each model on the unseen test set data.
> - Model Selection: Identifying the model with the lowest mean squared prediction error as the optimal choice for prediction purposes.
---
### 7. Model Selection in R
---
> **1. Implementing Model Selection Methods in R**  
> - Data Source: Analysis of a dataset from a 2018 paper on acoustic properties of woven fabrics.
> - Variables: Focus on absorption coefficient (acoustic1) and predictors like thickness, diameter, perforation, weight, stiffness, and air permeability.
> - Initial Data Check: Ensuring no missing values and data integrity for analysis.

> **2. Correlation Analysis and Full Model Fitting**  
> - Correlation: Examination of relationships between acoustic1 and predictors such as perforation, air permeability, and thickness.
> - Full Model: Fitting a model with acoustic1 as response and all other variables as predictors.
>   - e.g., Several predictors showing high p-values indicating lack of statistical significance.

> **3. Backward Elimination Process**  
> - Procedure: Removing predictors with the highest p-value iteratively to refine the model.
> - Criteria: Setting a p-value threshold (e.g., 0.15) to determine removal of predictors.
> - Result: Achieving a model with predictors having p-values below the set threshold.

> **4. Caution with Selection Methods**  
> - Limitation: Backward and forward selection methods may not reliably identify the best explanatory or predictive model.
> - Issue Highlight: Exclusion of thickness, a highly correlated predictor, due to multicollinearity.

> **5. Criterion-Based Model Selection Techniques**  
> - AIC Introduction: Formula involving number of parameters and residual sum of squares to aid in model selection.
> - Model Comparison: Utilizing AIC, along with BIC and adjusted R squared, to balance fit and complexity.

> **6. Model Fitting and Selection with regsubsets**  
> - regsubsets Function: Streamlining the process of fitting models with varying predictor numbers.
> - Model Evaluation: Using AIC to identify the model with the lowest value, indicating optimal choice.
>   - e.g., Three predictor model with the smallest AIC.

> **7. Adjusted R Squared and BIC Comparison**  
> - Adjusted R Squared: Identifying a model with the highest value for a given number of predictors.
> - BIC Agreement: Sometimes aligning with AIC in model choice, emphasizing prediction over explanation.
> - Expert Consultation: Highlighting the importance of domain expertise in final model selection.
---
### 8. The Problem of Collinearity
---
> **1. Introduction to Collinearity in Linear Regression**  
> - Collinearity: Situation where some predictors are closely related to others, making it hard to identify their unique contributions.
> - Linear Regression: Relies on design matrix X and relation X'X to compute least squares estimates, which may fail in the presence of multicollinearity.

> **2. Root of the Invertibility Issue**  
> - X'X Invertibility: Requires non-dependence between the columns of X for a unique least squares problem solution.
>   - e.g., X having one column as a constant multiple of another, like converting height from feet to centimeters.
> - Multicollinearity: Subtler case with no exact, but rather approximate, dependences that render X'X difficult to numerically invert.

> **3. Consequences of High Collinearity**  
> - Over-sensitiveness: Beta-hat's calculation becomes hard to interpret due to the fragility of X'X inversion under a multicolinearity situation.
> - Distorted Delineations: X'X ill-conditioned making the pi parameter in the model misleading, as assumptions on a specific metric may not hold, like a particular effect on X causing an outcome on Y.

> **4. Etiology of Collinearity**  
> - Reflection of Exogenous Relations: Arises from mis-specified models and data limitations (few data points vs. many predictors).
> - Model Mis-Specification and Consequence: Incorporating predictors not causally affecting the outcome and omitting one of the highly related predictive variables for the best modal fit.

> **5. Strategies for Taming Reduction**  
> - Considerate Feature Exploration: Based on product estimation data, pursue a careful, simplistic regularizement to distate appropriate parameters.
> - Obligatory Simplification: Narrowing down the best decision estimate model might require a solver's penalization to distinguish the prismatic "invisible" yet graphical outcomes. 

> **6. Mis-Specification vs. Data Property**  
> - Statistical Mis-Specification: Incorrect model assumptions leading to collinearity.
> - Lack of Information: Insufficient data to clearly differentiate the impact of predictors.

> **7. Implications of Multicollinearity**  
> - Parameter Interpretation: A unit increase in a specific X doesn't translate to a clear differential Y effect, illustrating both a real application problem and a model-sensory disarrangement.
> - Delineation Challenge: Encompasses a gainset for project goals and strategy, with real-port data to problematize on a calculated response.
---
### 9. Diagnosing Multicollinearity
---
> **1. Identifying Multicollinearity in Datasets**  
> - Challenge: Multicollinearity detection can be complex, with no single method guaranteeing identification.
> - Strategy: Employing multiple methods concurrently may aid in recognizing multicollinearity.

> **2. Pairwise Correlations**  
> - Basic Method: Utilizing correlation matrices to spot high correlations between predictors.
>   - e.g., If one predictor is highly correlated with another, consider removing one to reduce redundancy.
> - Decision Criteria: The choice of which predictor to remove depends on whether the goal is prediction or explanation.

> **3. Beta Estimates and Standard Errors**  
> - Imprecise Estimates: Multicollinearity can lead to large standard errors for beta estimates, hinting at potential issues.
>   - e.g., Unexpected signs in beta estimates may indicate multicollinearity, especially if contrary to theoretical expectations.

> **4. Variance Inflation Factor (VIF)**  
> - Concept: Measures how much the variance of a coefficient is inflated due to linear relations among predictors.
>   - e.g., A VIF greater than 10 suggests significant multicollinearity; values between 5 and 10 warrant further investigation.

> **5. Condition Number**  
> - Definition: A measure derived from the ratio of the largest to the smallest eigenvalue of the X'X matrix, indicating matrix condition.
>   - e.g., A condition number greater than 30 suggests an ill-conditioned matrix, likely due to multicollinearity.
> - Calculation: The Kappa function in R can compute the condition number efficiently.
---
### 10. Multicollinearity Solutions in R
---
> **1. Techniques for Handling Multicollinearity**  
> - Overview: Identifying methods to address multicollinearity, including practical R code applications.
> - Methods: Three primary approaches to mitigate multicollinearity effects.

> **2. Removing Predictors**  
> - Initial Approach: Eliminating one or more predictors to alleviate multicollinearity.
>   - e.g., If XJ is nearly a linear combination of other variables, removing XJ could solve the problem.
> - Considerations: Importance of causal relationships in explanatory models and less concern in predictive models.

> **3. Alternative Estimation Methods**  
> - Ridge Regression: Introduces bias to reduce variance in estimators, beneficial in the presence of multicollinearity.
> - Principal Component Analysis (PCA): A dimension reduction tool to simplify models by condensing predictors into principal components.

> **4. Diagnosing Multicollinearity in R**  
> - Tools: Utilizing condition number and variance inflation factors (VIF) to detect multicollinearity.
> - Example Data: Analysis of fabric data showing high condition numbers and moderately high VIFs indicating multicollinearity.

> **5. Model Selection to Reduce Multicollinearity**  
> - Strategy: Employing model selection techniques to derive a reduced model with fewer predictors.
>   - e.g., A reduced model with predictors like perforation, weight, and air permeability.
> - Outcome: Reduction in VIFs, though some indicators like the condition number may remain elevated.

> **6. Correlation Matrix Analysis**  
> - Insight: High pairwise correlations between predictors like air permeability and perforation signal multicollinearity.
> - Decision Making: For prediction, removing one of the highly correlated predictors may suffice; for explanation, deeper investigation is needed.

> **7. Practical Application and Decision Making**  
> - Testing: Evaluate models by removing predictors alternately and comparing mean squared prediction error on a test set.
> - Goal Orientation: Choice of model adjustments based on whether the objective is prediction accuracy or understanding causal relationships.
---