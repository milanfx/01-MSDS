---
layout: page
title: M1 - Regression Introduction
permalink: /M1-Regression-Introduction/
---

<h3>01 - Statistical Modeling Frameworks</h3>

<h4>1. Introduction to Statistical Modeling</h4>

> - Focus: Linear regression models.  
> - Application: Broad applicability across sciences, business, and other domains.  
> - Skills: Use data for theory development, predictions, and data-driven decisions.

<h4>2. Relevance of Statistical Models</h4> 

> - Example: Predicting wildfire occurrences.  
> - Inputs: Temperature, relative humidity, fuel density, etc.  
>   - e.g., Similar to an audio mixer with various inputs affecting the output.  
> - Challenge: Statisticians cannot control inputs like an audio engineer can.  
> - Determinism vs. Stochasticity: Relationships between inputs and outputs are stochastic, not deterministic.

<h4>3. Explanation and Prediction</h4>

> - Tasks: Differentiating between explaining relationships and predicting outcomes.  
> - Example: Wildfire modeling to predict significant wildfires or understand input-output relationships.

<h4>4. Key Questions in Statistical Modeling</h4>

> - Variable selection: Determining relevant input variables.  
> - Impact of changes: How changes in one input affect the output.  
>   - e.g., Does a 10-degree increase in temperature have the same effect across different temperature ranges?  
> - Causal relationships: Exploring if and how inputs cause changes in outputs.

<h4>5. Empirical Questions and Data Collection</h4>

> - Start: With a pertinent empirical question.  
> - Example 1: Likelihood of large wildfires in Rocky Mountain National Park.  
> - Example 2: Safety of cycling in different seasons in Boulder.  
> - Example 3: Impact of social media advertising on product sales.

<h4>6. Statistical Units and Sampling</h4>

> - Units: Members of the entity set being studied.  
> - Example: Residents of Boulder, Colorado, with diverse exercise habits.  
> - Variables: May include exercise type, frequency, age, and pre-existing conditions.  
> - Sampling: Collecting a representative subset of the population to model relationships.

<h3>2. Concept Validity Assumption - Operationalization</h3>

<h4>1. Concept Validity and Operationalization</h4>

> - Importance: Fundamental assumptions in statistical modeling.  
> - Operationalization: Process of defining a concept in measurable terms.  
> - Validity: Extent to which a dataset or tool measures what it claims.

> **2. Example of Operationalization**  
> - Context: Cycling safety during COVID-19 pandemic.  
> - Research Question: Differences in cycling safety between summer and winter.  
> - Data Relevance: Identifying relevant data to measure the concept of safety.

> **3. Interpreting Safety**  
> - Cautious Interpretation: Includes minor injuries like scrapes and bruises.  
> - Venturesome Interpretation: Focuses on severe injuries or death.  
> - Decision Making: Choosing an interpretation based on research goals.

> **4. Challenges in Operationalization**  
> - Data Availability: Difficulty in finding data that matches the intended concept.  
> - Mismatch: Risk of operationalizing a concept in a way that doesn't match the intended meaning.  
> - Example: Studies on winter cycling safety may not account for minor injuries, leading to potential misunderstandings.

> **5. Ensuring Validity**  
> - Alignment: Ensuring data analysis maps onto the research question accurately.  
> - Data Collection: The importance of collecting new data that accurately reflects the concept of interest.  
> - Awareness: Recognizing the potential for mismatch between operationalized concepts and data analysis.
---
### 3. Linear Regression Model
---
> **1. Introduction to Linear Regression**  
> - Motivation: Extension of basic statistical inference concepts like hypothesis testing and estimation theory.  
> - Components: Identification of systematic and random components in models.  
> - Differentiation: Distinction between linear and non-linear models.  
>   - e.g., Linear models involve a direct proportional relationship between variables.

> **2. Basic Statistical Inference**  
> - Data Points: Introduction to terms like sample, random sample, and distributions.  
> - Goal: Estimation of mean (Mu) or hypothesis testing about Mu using sample data.  
>   - e.g., Using y-bar as an estimator for Mu.  
> - Variation in Mu: Consideration of scenarios where Mu depends on other variables.

> **3. Variables and Relationships**  
> - Mean Dependency: Introduction to the concept where Mu depends on other variables and fixed constants.  
> - Linear Relationship: Exploration of linear relationships, such as an intercept plus a slope times x.  
>   - e.g., The mean value of a variable having a linear relationship with another variable.

> **4. Defining Terms in Linear Regression**  
> - Response Variable: The variable y, used to predict or explain outcomes based on other variables (x1 through xp).  
> - Predictors: Variables (x1 through xp) used to predict the response variable.  
>   - e.g., Also referred to as inputs, independent variables, explanatory variables, or features.  
> - Continuity: Assumption that both the response variable and predictors are continuous.  

> **5. The Linear Relationship**  
> - Equation: Description of the linear equation relating the response variable to predictors.  
> - Measurement and Error: Acknowledgment of measurement error in data, leading to variations from the exact linear relationship.  
>   - e.g., Introduction of the epsilon term to account for random noise in measurements.

> **6. Visualization of Linear Relationships**  
> - Exact vs. Noisy Relationships: Comparison of ideal linear relationships and practical noisy data.  
>   - e.g., Plots illustrating perfect alignment vs. data with noise around a linear trend.

> **7. Objectives of Linear Regression**  
> - Prediction: Using predictors to estimate unseen response variables.  
> - Explanation: Understanding how predictors affect the response variable.  
> - Causality: Discussion on the causal relationship between predictors and the response, and the complexity of establishing causality.  
---
### 4. Linear Regression Matrix
---
> **1. Writing Linear Regression in Matrix Notation**  
> - Introduction: Transition from scalar to matrix notation in linear regression.  
> - Notation: Vectors are typically column vectors; transpose used for space-saving.  
> - Vectors and Matrices: Response (Y) and predictors (X) represented as vectors and matrices.  
>   - e.g., Y as a vector of n measurements, X as a design matrix with p predictors.

> **2. Design Matrix Explanation**  
> - Design Matrix (X): Incorporation of predictors and a column of ones for intercept.  
> - Dimensions: X is an n by p+1 matrix, accommodating the intercept and p predictors.  
>   - e.g., First column is a vector of ones, followed by columns for each predictor.

> **3. Parameter Vector**  
> - Parameters: Beta-naught through Beta-p represented in a parameter vector.  
> - Error Vector: Grouping of error terms (epsilon) into an n-component vector.  
> - Model Equation: Compact representation of the linear regression model using matrix-vector equation Y = X Beta + Epsilon.

> **4. Dimensional Analysis**  
> - Compatibility: Ensuring the dimensions of matrices and vectors align for multiplication.  
> - Result: Y, Beta, and Epsilon vectors’ dimensions ensure proper execution of linear algebra operations.  

> **5. Flexibility of Linear Models**  
> - Nonlinear Transformations: Linear models can adapt to certain nonlinear relationships through transformations.  
>   - e.g., Modeling y = Beta-naught + Beta-one * sine(x) by treating sine(x) as a separate variable.  
>   - e.g., Transforming y = e^(Beta-naught + Beta-one * x) into a linear model by taking the logarithm.

> **6. Limitations and Nonlinear Contexts**  
> - Nonlinear Parameters: Challenges in modeling when parameters are part of nonlinear functions.  
>   - e.g., y = Beta-naught + Beta-one * sine(Beta-two * x) defies simple linear transformation.  
>   - e.g., Complex models involving parameters in bases and exponents, indicating the need for nonlinear modeling techniques.
---
### 5. Linear Regression Assumptions
---
> **1. Assumptions for Linear Regression**  
> - Importance: Assumptions underpin the validity of linear regression analysis.  
> - Framework: Four key assumptions in descending order of importance.  
>   - e.g., Linearity, independence of measurements, homoscedasticity, and normal distribution of residuals.

> **2. Linearity Assumption**  
> - Definition: A linear relationship between the response and predictors.  
> - Equation: Y = Xβ + ε, where Y is the response vector, X is the design matrix, β is the parameter vector, and ε is the error term.  
> - Flexibility: Allows for transformations of predictors to fit into a linear model.  
>   - e.g., Nonlinear transformations treated as variables to maintain a linear relationship.

> **3. Independence Among Response Measurements**  
> - Principle: Response measurements must be independent of each other, given the predictors.  
> - Example Context: Sales predictions in different companies should not influence each other.  
> - Implication: Probabilistic independence implies zero covariance between different response measurements (Yi and Yj or εi and εj).

> **4. Homoscedasticity (Constant Variance) Assumption**  
> - Definition: All response measurements have the same variance, σ².  
> - Significance: Each observation contributes equally to the information about the mean.  
>   - e.g., Variance of εi is constant across all i, ensuring uniform information distribution.

> **5. Normal Distribution of Response Measurements**  
> - Requirement: Response measurements follow a normal distribution with mean μ = Xβ and constant variance σ².  
> - Basis: Assumes error terms ε are IID normal with mean 0 and variance σ².  
> - Role in Analysis: Essential for the theoretical foundation of linear regression model's inference and prediction accuracy.
---
### 6. Linear Regression Appropriateness
---
> **1. Statistical Models and Assumptions**  
> - Overview: Examination of statistical models and underlying assumptions.  
> - Validity: Importance of assumptions for model validity.  
> - Focus: Detailed look into linear regression model, matrix representation, and key assumptions.

> **2. Appropriateness of Linear Regression**  
> - Criteria: Determining when linear regression fits the data.  
> - Theory-Based Models: Use of theoretical laws (e.g., Hooke's law in physics) indicating linear relationships.  
> - Past Studies: Reliance on previous research to guide model selection.  
> - Data Exploration: Use of exploratory data analysis to form hypotheses about data relationships.

> **3. Avoiding Double-Dipping**  
> - Problem: The issue with using the same dataset for hypothesis generation and testing.  
> - Solutions:  
>   - Pre-specifying hypotheses before data analysis.  
>   - Splitting data into exploratory and testing sets to prevent biased statistical inference.

> **4. Linear Regression Flexibility**  
> - Misconception: Linear regression is not limited to strictly linear relationships between variables.  
> - Parameters vs. Predictors: Linearity in parameters allows for modeling nonlinear relationships between predictors and response.  
>   - e.g., Quadratic or polynomial relationships can be modeled with linear regression.  
> - Limitations: Acknowledgment of nonlinear data that cannot be addressed by linear regression.
---
### 7. Linear Regression Interpretation
---
> **1. Interpretability of Linear Regression Models**  
> - Importance: Understanding how to interpret the regression model and its components.  
> - Components: Focus on error terms and model parameters for interpretability.

> **2. Understanding the Error Term**  
> - Concept: Visualization of the error term in linear regression.  
> - True Regression Line: Representation of the systematic and random components of the model.  
> - Error Distribution: The role of normal distribution with mean 0 and variance Sigma squared in determining the spread of data points around the true line.  
>   - e.g., For a fixed x, data points distribute normally around the predicted y value on the true regression line.

> **3. Interpreting Model Parameters**  
> - Intercept (Beta naught): Average value of the response when the predictor x is equal to zero.  
> - Slope (Beta one): Average change in the response associated with a one unit increase in the predictor.  
>   - Importance of Context: Adjusting units for meaningful interpretation, like income changes affecting another variable.

> **4. Multiple Linear Regression Context**  
> - Intercept Interpretation: Average value of Y when all predictors are zero.  
> - Slope Terms Interpretation: Average change in Y associated with a one unit increase in a specific predictor, holding other predictors constant.  
>   - Adjusting for Predictors: The value of interpreting changes in Y adjusting for the effects of other variables.
---