---
### 1. Linear Regression Diagnostic Methods
---
> **1. Linear Regression Model Assumptions**  
> - Linearity: Assumes a linear relationship between the response variable and parameters.  
> - Independence: Response measurements are independent from one another.  
> - Homoskedasticity: Assumes constant variance across all response measurements.  
> - Normality: Error terms or response terms are normally distributed.

> **2. Diagnosing Assumption Violations**  
> - Model fitting and analysis: Techniques to assess if the model assumptions hold for the data.  
> - Numerical vs. graphical techniques: Statisticians often favor graphical methods for their insightful representations of model fit.

> **3. Validity of Data**  
> - Concept of validity: Measures the extent to which data or tools measure what they claim to.  
> - Assessment of validity: Ideally involves multiple measurements or comparisons to expert opinions or established standards.  
>   - e.g., Comparing new depression measurement tools to expert psychiatrist opinions or established inventories.

> **4. Collaboration with Domain Experts**  
> - Importance of domain expertise: Validity assessment should involve experts familiar with the science or business application.  
> - Diagnostic methods and validity: Diagnostic techniques focus on model assumption deviations, not on the validity of the data set for answering research questions.
---
### 2. Linearity Assumption
---
> **1. Assessing Linearity Assumption in Linear Regression**  
> - Model correctness: The relationship between the response and parameters must be linear.  
> - Linearity specifics: Expected value of the response should be a linear function of each predictor, holding other predictors constant.

> **2. Implications of Violating Linearity**  
> - Biased least squares estimator: Non-linearity leads to bias in parameter estimation.  
> - Misinterpretation: Incorrect model specification affects the explanatory power and interpretation of the model.  
> - Misleading inferences: Violations impact the reliability of statistical tests like t-tests and F-tests.  
> - Prediction accuracy: Non-linearity decreases the predictive accuracy of the model.

> **3. Graphical Methods for Diagnosing Linearity Violations**  
> - Fitted vs. Observed Values: A scatter plot should ideally show data points scattered around the line y = ŷ, indicating close predictions to actual observations.  
>   - e.g., Curvature in this plot suggests systematic prediction errors, indicating non-linearity.
> - Residuals Analysis: Residuals should appear random and centered around 0 with a constant variance, without any discernible patterns.  
>   - e.g., Curvature or systematic patterns in a plot of residuals vs. fitted values indicate a misspecified model.

> **4. Validity of Residuals in Model Assessment**  
> - Residuals fit: Ideally, the non-linear fit (e.g., gray curve) through residuals should be as flat as possible, indicating random noise rather than systematic error.  
> - Evidence against linearity: Presence of structure or trend in residuals suggests incorrect model structure, challenging the linearity assumption.
---
### 3. Independence Assumption
---
> **1. Independence Assumption in Linear Regression**  
> - Core assumption: Response measurements or error terms are independent.  
> - Importance: Independence is crucial for accurate inference and prediction.  
> - Violation sources: Data measured in space or time, or any ordering that introduces correlation.

> **2. Detecting Independence Violations**  
> - Challenges: Identifying correlation patterns due to numerous possible data orderings.  
> - Methods: Includes plotting residuals vs. index, successive residual plots, and the Durbin-Watson test.

> **3. Residuals vs. Index Plot**  
> - Purpose: Identifies sequences or clusters of residuals indicating correlation.  
> - Index determination: May represent time or another relevant ordering of data points.  
>   - e.g., Cyclical patterns in residuals suggest independence assumption violations.

> **4. Successive Residual Plot**  
> - Analysis: Examines the correlation between consecutive residuals.  
> - Limitation: Primarily detects successive correlations, missing more complex dependency structures.

> **5. Durbin-Watson Test**  
> - Focus: Tests for autocorrelation in error terms, especially for successive measurements.  
> - Test statistic `D`: A value close to 2 suggests no autocorrelation; values significantly lower than 2 indicate positive correlation.

> **6. Addressing Independence Violations**  
> - Generalized Least Squares (GLS): Adjusts for known correlation structures in error terms.  
> - Variance-Covariance Matrix: Essential for GLS, often unknown making direct application challenging.  
> - Specialized Methods: Time series and spatial statistics offer approaches for estimating the correlation structure.
---
### 4. Constant Variance Assumption
---
> **1. Constant Variance Assumption in Regression**  
> - Homoskedasticity: Assumes equal variance (σ²) across all response measurements.  
> - Variance-covariance matrix: Represented as σ² times the identity matrix, indicating independence and constant variance.

> **2. Residuals and Error Variance**  
> - Residuals estimation: Serve as estimators for error terms, but don't inherently possess constant variance.  
> - Variance of residuals: Derived from the identity minus the hat matrix, showing variance differences among residuals.

> **3. Checking Constant Variance**  
> - Residuals vs. Fitted Plot: Used to identify variance consistency across different fitted values.  
> - Residuals vs. Potential Predictor Plot: Indicates whether including a specific predictor could stabilize variance.

> **4. Evidence of Non-Constant Variance**  
> - Trumpeting pattern: Residuals displaying larger variance for higher or lower fitted values suggest heteroskedasticity.

> **5. Addressing Variance Violations**  
> - Response transformation: Applying square root or log transformations to stabilize variance.  
> - Including missing predictors: Incorporating relevant predictors into the model to address variance instability.  
> - Weighted/Generalized Least Squares: Adjusts the estimation process for known variance differences among responses.
>   - Weighted Least Squares in R: Utilizes the `lm` function with a `weights` argument for variance adjustment.
---
### 5. Normality Assumption
---
> **1. Normality Assumption in Linear Regression**  
> - Normality for inference: Essential for conducting hypothesis tests and calculating confidence intervals.  
> - Deviations: Slight deviations are tolerable; significant deviations impact statistical inferences.

> **2. Diagnosing Normality Violations**  
> - Q-Q Plot: Compares quantiles of residuals against a theoretical normal distribution to identify deviations.  
> - Residuals vs. Fitted Plot: Should show random scatter around y=0 without significant outliers.  
> - Shapiro-Wilk Test: Formal hypothesis test assessing if residuals come from a normal distribution.

> **3. Q-Q Plot Analysis**  
> - Normal data simulation: Shows residuals lining up along the y=x line, indicating normality.  
> - Non-normal data (Poisson): Deviations from y=x line, suggesting non-normality.

> **4. Residuals vs. Fitted Values for Normality**  
> - Correct model: Scatter around y=0 with minimal curvature indicates no significant deviation from normality.  
> - Incorrect model (Poisson errors): Patterns or non-random scatter suggest non-normal distribution of residuals.

> **5. Shapiro-Wilk Test for Normality**  
> - Test sensitivity: Very sensitive to large datasets, potentially indicating minor deviations from normality.  
> - Preference for visualization: Plots provide a more nuanced understanding of deviations than numerical thresholds.

> **6. Addressing Deviations from Normality**  
> - Data transformation: Applying transformations like log or square root to stabilize variance and improve normality.  
> - Model change: Considering generalized linear models (GLM) for more flexibility with different response distributions.
---
### 6. Diagnostics in R
---
> **1. Implementing Diagnostic Techniques in R**  
> - Data loading: Load marketing data from the web.
> - Model fitting: Fit a linear regression model with marketing budgets as predictors and sales as the response.

> **2. Diagnostic Plots in Base R and ggplot**  
> - Base R method: Use the plot function on the linear model object for diagnostic plots.
>   - e.g., Four diagnostic plots can be generated.
> - ggplot method: Create a data frame with necessary quantities for diagnostics to produce aesthetically pleasing plots.
>   - e.g., Fitted values, residuals, observed values, and predictors included.

> **3. Assessing Linearity**  
> - Plot analysis: Examine plot of fitted values against observed values to assess linearity.
>   - e.g., Systematic deviations from the y=x line indicate model misfit.
> - Observations: Under-prediction at high observed values, over-prediction in the middle, and variability at low values.

> **4. Residuals Versus Fitted Values**  
> - Purpose: Collaborate linearity assessment with residuals versus fitted values plot.
>   - e.g., Non-linear structure suggests mis-specified model.
> - Desired outcome: Random scatter around y=0 indicating correct model specification.

> **5. Normality Assumption**  
> - QQ plot analysis: Assess normality through qq plot comparing residuals' quantiles with theoretical quantiles.
>   - e.g., Deviations for low and high values indicate normality assumption may not be satisfied.

> **6. Non-Constant Variance Assumption**  
> - Variance assessment: Examine residuals versus fitted values for evidence of non-constant variance.
>   - e.g., Lack of clear "trumpeting" pattern suggests constant variance across fitted values.

> **7. Independence Assumption**  
> - Successive residuals: Use plots to assess if successive errors are correlated, indicating independence.
>   - e.g., Low correlation in plots of successive residuals.
> - Residuals versus index: Check for patterns that could indicate violations of independence.
>   - e.g., No significant wavy structure or patterns detected.

> **8. Correlation in Residuals**  
> - Structured residuals: Identify structure in residuals when ordered by predictors, suggesting potential correlation.
>   - e.g., Curvature and variability in residuals ordered by YouTube budget.
> - Model structure: Consideration of additional predictors to explain systematic variability and meet assumptions.
---