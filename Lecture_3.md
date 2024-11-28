# Lecture 3: Ordinary Least Squares (OLS) & Multiple Regression Analysis

*Chapters 2.1, 2.2, 2.3, 3.1-3.5*

## 1. Simple Regression Model (OLS)

### 1.1 Introduction to OLS

**Model Specification:**

>$$
>y = \beta_0 + \beta_1 x + u
>$$
>- **$y$:** Dependent variable (outcome)
>- **$x$:** Independent variable (explanatory/regressor)
>- **$u$:** Error term (captures unobserved factors)
>- **$\beta_0$:** Intercept
>- **$\beta_1$:** Slope (effect of $x$ on $y$)

### 1.2 Intuition and Assumptions of OLS

1. **Zero Mean Error:**
   $$E(u) = 0$$
   - Ensured by including $\beta_0$ in the model.

2. **Mean Independence:**
   $$E(u|x) = E(u) = 0$$
   - Implies no linear relationship between $u$ and $x$.

3. **Population Regression Function:**
   $$E(y|x) = \beta_0 + \beta_1 x$$
   - The average of $y$ changes with $x$.
   - Individual observations do not lie exactly on the regression line.

### 1.3 Terminology

- **OLS Regression Line:**
  $$\hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x$$

- **Fitted Value ($\hat{y}_i$):** Predicted $y$ for a given $x_i$.

- **Residual ($\hat{u}_i$):**
  $$\hat{u}_i = y_i - \hat{y}_i$$
  - Difference between actual and fitted values.
  - Residuals are inferred from data; errors are unobserved.

### 1.4 Algebraic Properties of OLS

1. **Residuals Sum to Zero:**
   $$\sum_{i=1}^n \hat{u}_i = 0$$

2. **Regression Line Passes Through the Mean:**
   $$\bar{y} = \hat{\beta}_0 + \hat{\beta}_1 \bar{x}$$

3. **Orthogonality:**
   $$\sum_{i=1}^n \hat{u}_i x_i = 0$$

4. **Decomposition of Total Sum of Squares (SST):**
   $$SST = SSR + SSE$$
   - **SSR (Regression Sum of Squares):** Explained variation.
   - **SSE (Error Sum of Squares):** Unexplained variation.

### 1.5 Goodness of Fit

- **R-squared ($R^2$):**
  $R^2 = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$
  - Measures the proportion of variance in $y$ explained by $x$.
  - **Interpretation:**
    - **$R^2 = 1$:** Perfect fit.
    - **$R^2 = 0$:** No explanatory power.
  - **Note:** $R^2$ ranges from 0 to 1.

### 1.6 Variance of the OLS Estimator

>$$Var(\hat{\beta}_j) = \frac{\sigma^2}{SST_j (1 - R_j^2)}$$
>
>- **$\sigma^2$:** Variance of the error term (unknown; estimated as $\hat{\sigma}^2$).
>- **$SST_j$:** Total sum of squares for regressor $x_j$.
>- **$R_j^2$:** R-squared from regressing $x_j$ on other regressors (measures multicollinearity).

**Standard Error:**
```math
se(\hat{\beta}_j) = \sqrt{Var(\hat{\beta}_j)}
```

**Components Explained:**

- **$\sigma^2$:**
  - Represents data noise.
  - Can be reduced by including more relevant variables.

- **$SST_j$:**
  - Larger $SST_j$ reduces variance.
  - Increases with sample size.

- **$R_j^2$:**
  - Higher $R_j^2$ (multicollinearity) increases variance.
  - **Note:** Perfect multicollinearity ($R_j^2 = 1$) is disallowed.

## 2. Multiple Regression Analysis

### 2.1 Introduction to Multiple Regression

**Model Specification:**
>$$
>y_i = \beta_0 + \beta_1 x_{1i} + \beta_2 x_{2i} + \dots + \beta_k x_{ki} + u_i \quad \quad i=1, \dots, n
>$$
>
>- **$y_i$:** Dependent variable
>- **$x_{1i}, \dots, x_{ki}$:** Independent variables (regressors)
>- **$u_i$:** Error term
>- **$\beta_0, \beta_1, \dots, \beta_k$:** Parameters

### 2.2 Interpretation of OLS Coefficients

- **Intercept ($\hat{\beta}_0$):** Predicted $y$ when all $x$'s are zero.
- **Slope ($\hat{\beta}_j$):** Change in $y$ for a one-unit change in $x_j$, holding other variables constant (ceteris paribus).

### 2.3 Algebraic Properties

Similar to simple OLS:

- **Residuals Sum to Zero:**
  $$\sum_{i=1}^n \hat{u}_i = 0$$

- **Regression Hyperplane Passes Through the Mean Vector:**
  $$\bar{y} = \hat{\beta}_0 + \hat{\beta}_1 \bar{x}_1 + \dots + \hat{\beta}_k \bar{x}_k$$

- **Orthogonality:**
  $$\sum_{i=1}^n \hat{u}_i x_{ij} = 0 \quad \forall j = 1, \dots, k$$

- **Decomposition of Total Sum of Squares (SST):**
  $$SST = SSR + SSE$$
  - **SSR:** Explained variation.
  - **SSE:** Unexplained variation.

### 2.4 Goodness of Fit

- **R-squared ($R^2$):**
  $$R^2 = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$$
  - Measures the proportion of variance in $y$ explained by all regressors.
  - **Properties:**
    - **$R^2$ increases** or **stays the same** when adding more regressors.
    - Not a reliable indicator for model selection.

### 2.5 Omitted Variable Bias (OVB)

**Definition:**
Occurs when a relevant variable is excluded from the model and is correlated with both the included regressor and the dependent variable.

**Example:**

True Model:
$$\text{wage}_i = \beta_0 + \beta_1 \text{educ}_i + \beta_2 \text{abil}_i + u_i$$

Estimated Model (Omitting $\text{abil}_i$):
$$\text{wage}_i = \beta_0 + \beta_1 \text{educ}_i + v_i \quad \text{where} \quad v_i = \beta_2 \text{abil}_i + u_i$$

**Bias in $\hat{\beta}_1$:**
$$\text{Bias}(\hat{\beta}_1) = \beta_2 \delta_1$$
- **$\delta_1$:** Relationship between $\text{educ}$ and $\text{abil}$.
- **Direction of Bias:**
  - **Downward:** If $\beta_2 \delta_1 < 0$.
  - **Upward:** If $\beta_2 \delta_1 > 0$.

### 2.6 Variance of the OLS Estimator

**Variance Formula:**
>$$Var(\hat{\beta}_j) = \frac{\sigma^2}{SST_j (1 - R_j^2)}$$
>
>- **$\sigma^2$:** Variance of the error term (unknown; estimated as $\hat{\sigma}^2$).
>- **$SST_j$:** Total sum of squares for regressor $x_j$.
>- **$R_j^2$:** R-squared from regressing $x_j$ on other regressors (measures multicollinearity).

**Standard Error:**

$$se(\hat{\beta}_j) = \sqrt{Var(\hat{\beta}_j)}$$

## 3. Assumptions of OLS

**General Assumptions (Applicable to Both Simple and Multiple Regression):**

1. **Linearity (A1):**
   - Model is linear in parameters.
   - Can include non-linear transformations of $x$ (e.g., $\log(x)$).

2. **Independence (A2):**
   - Observations are independently and identically distributed (i.i.d.).
   - Violations include non-random sampling and dependent observations (e.g., time series).

3. **No Perfect Multicollinearity (A3):**
   - Regressors are not perfect linear combinations of each other.
   - Example of perfect multicollinearity:
     $$y = \beta_0 + \beta_1 \text{income} + \beta_2 \left(\frac{\text{income}}{100}\right) + u$$

4. **Zero Conditional Mean (A4):**
   $$E(u|X) = 0$$
   - No omitted variable bias; errors are uncorrelated with regressors.
   - **Implications:**
     - $E(u) = 0$
     - $\text{Cov}(u, x_j) = 0$ for all $j$
     - $E(y|X) = \beta_0 + \beta_1 x_1 + \dots + \beta_k x_k$

5. **Homoskedasticity (A5):**
   $$Var(u|X) = \sigma^2$$
   - Constant variance of errors.
   - **Heteroskedasticity:** When $Var(u|X)$ varies with $X$.

6. **Normality (A6, Optional):**
   $$u \sim N(0, \sigma^2)$$
   - Useful for hypothesis testing and constructing confidence intervals.

**Detailed Assumption Explanations:**

- **A1 (Linearity):**
  - Ensures the model correctly specifies the relationship between variables.
  - Non-linear relationships can be modeled using transformations.

- **A2 (Independence):**
  - Critical for the validity of inference.
  - Violations can lead to biased standard errors and invalid hypothesis tests.

- **A3 (No Perfect Multicollinearity):**
  - Essential for the uniqueness of OLS estimates.
  - High but imperfect multicollinearity increases variance of estimates.

- **A4 (Zero Conditional Mean):**
  - Fundamental for unbiasedness of OLS estimators.
  - Violations often arise from omitted variables, measurement errors, or simultaneity.

- **A5 (Homoskedasticity):**
  - Ensures efficient estimates and valid standard errors.
  - Heteroskedasticity requires robust standard errors or other corrective measures.

- **A6 (Normality):**
  - Not required for OLS estimates to be unbiased or consistent.
  - Necessary for exact inference in small samples.

## 4. Key Takeaways

- **OLS** is a foundational method for estimating linear relationships between variables under specific assumptions.
  
- **Simple Regression Model:**
  - Focuses on the relationship between one dependent and one independent variable.
  - Key concepts include the regression line, residuals, and $R^2$.

- **Multiple Regression Analysis:**
  - Extends OLS to include multiple independent variables.
  - Allows for controlling multiple factors, enhancing causal inference.
  - Introduces complexities like multicollinearity and omitted variable bias.

- **Goodness of Fit ($R^2$):**
  - Indicates the proportion of variance explained by the model.
  - Does not imply causality or model correctness.

- **Assumptions:** 
  - Critical for the validity of OLS estimates.
  - Violations can lead to biased, inconsistent, or inefficient estimates.

- **Omitted Variable Bias (OVB):**
  - Highlights the importance of including all relevant variables to avoid biased estimates.
  - Understanding OVB is crucial for building reliable models.

- **Variance and Standard Errors:**
  - Essential for hypothesis testing and constructing confidence intervals.
  - Influenced by factors like sample size, multicollinearity, and error variance.
