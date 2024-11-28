# Lecture 3: Ordinary Least Squares (OLS) & Multiple Regression Analysis

*Chapters 2.1, 2.2, 2.3, 3.1-3.5*

## 1. Introduction to OLS (Simple Regression Model)

**Model Specification:**
$$
y = \beta_0 + \beta_1 x + u
$$

- **$y$:** Dependent variable (outcome)
- **$x$:** Independent variable (explanatory/regressor)
- **$u$:** Error term (captures unobserved factors)
- **$\beta_0$:** Intercept
- **$\beta_1$:** Slope (effect of $x$ on $y$)

## 2. Intuition and Assumptions of OLS

1. **Zero Mean Error:**
   
$$E(u) = 0$$
   - Ensured by including $\beta_0$ in the model.

3. **Mean Independence:**
   
$$E(u|x) = E(u) = 0$$
   - Implies no linear relationship between $u$ and $x$.

4. **Population Regression Function:**
   
$$
   E(y|x) = \beta_0 + \beta_1 x
$$
   - The average of $y$ changes with $x$.
   - Individual observations do not lie exactly on the regression line.

## 3. OLS Terminology

- **OLS Regression Line:**
  
$$
  \hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x
$$

- **Fitted Value ($\hat{y}_i$):** Predicted $y$ for a given $x_i$.

- **Residual ($\hat{u}_i$):**
  
$$
  \hat{u}_i = y_i - \hat{y}_i
$$
  - Difference between actual and fitted values.
  - Residuals are inferred from data; errors are unobserved.

## 4. Algebraic Properties of OLS

1. **Residuals Sum to Zero:**
   
$$\sum_{i=1}^n \hat{u}_i = 0$$

3. **Regression Line Passes Through the Mean:**
   
$$
   \bar{y} = \hat{\beta}_0 + \hat{\beta}_1 \bar{x}
$$

4. **Orthogonality:**
   
$$\sum_{i=1}^n \hat{u}_i x_i = 0$$

5. **Decomposition of Total Sum of Squares (SST):**
   
$$SST = SSR + SSE$$

   - **SSR (Regression Sum of Squares):** Explained variation.
   - **SSE (Error Sum of Squares):** Unexplained variation.

## 5. Goodness of Fit

- **R-squared ($R^2$):**
  
$$R^2 = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$$

  - Measures the proportion of variance in $y$ explained by $x$.
  - Ranges from 0 to 1.
  - **Interpretation:**
    - **$R^2 = 1$:** Perfect fit.
    - **$R^2 = 0$:** No explanatory power.

## 6. Multiple Regression Analysis

**Model Specification:**

$$y_i = \beta_0 + \beta_1 x_{1i} + \beta_2 x_{2i} + \dots + \beta_k x_{ki} + u_i \quad \quad i=1, \dots, n$$

- **$y_i$:** Dependent variable
- **$x_{1i}, \dots, x_{ki}$:** Independent variables (regressors)
- **$u_i$:** Error term
- **$\beta_0, \beta_1, \dots, \beta_k$:** Parameters

### 6.1 Interpretation of OLS Coefficients

- **Intercept ($\hat{\beta}_0$):** Predicted $y$ when all $x$'s are zero.
- **Slope ($\hat{\beta}_j$):** Change in $y$ for a one-unit change in $x_j$, holding other variables constant (ceteris paribus).

### 6.2 Algebraic Properties

Similar to simple OLS:
- Residuals sum to zero.
- Residuals are orthogonal to each regressor.
- Regression hyperplane passes through the mean vector $(\bar{y}, \bar{x}_1, \dots, \bar{x}_k)$.
- **SST = SSR + SSE**

## 7. Assumptions of OLS

1. **Linearity (A1):**
   - Model is linear in parameters.
   
2. **Independence (A2):**
   - Observations are independently and identically distributed (i.i.d.).
   
3. **No Perfect Multicollinearity (A3):**
   - Regressors are not perfect linear combinations of each other.
   
4. **Zero Conditional Mean (A4):**
   
$$E(u|X) = 0$$
   - No omitted variable bias; errors are uncorrelated with regressors.
   
6. **Homoskedasticity (A5):**
   
$$Var(u|X) = \sigma^2$$
   - Constant variance of errors.
   
7. **Normality (A6, Optional):**
   
$$u \sim N(0, \sigma^2)$$
   - Useful for hypothesis testing.

### 7.1 Assumption Details

- **A1 (Linearity):**
  - The relationship between dependent and independent variables is linear in parameters.
  - Non-linear transformations of $x$ (e.g., $\log(x)$ ) can be included.

- **A2 (Independence):**
  - Sample must be randomly drawn from the population.
  - Violations include non-random sampling and dependent observations (e.g., time series).

- **A3 (No Perfect Multicollinearity):**
  - Prevents exact linear relationships among regressors.
  - Example of perfect multicollinearity:
$$y = \beta_0 + \beta_1 \text{income} + \beta_2 \left(\frac{\text{income}}{100}\right) + u$$

- **A4 (Zero Conditional Mean):**
  - Ensures unbiasedness of OLS estimates.
  - Violations lead to omitted variable bias, measurement error, etc.

- **A5 (Homoskedasticity):**
  - Constant variance of error terms.
  - Heteroskedasticity occurs when $Var(u|X)$ varies with $X$.

## 8. Omitted Variable Bias (OVB)

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

## 9. Variance of the OLS Estimator

**Variance Formula:**
$$Var(\hat{\beta}_j) = \frac{\sigma^2}{SST_j (1 - R_j^2)}$$

- **$\sigma^2$:** Variance of the error term (unknown; estimated as $\hat{\sigma}^2$).
- **$SST_j$:** Total sum of squares for regressor $x_j$.
- **$R_j^2$:** R-squared from regressing $x_j$ on other regressors (measures multicollinearity).

**Standard Error:**
$$se(\hat{\beta}_j) = \sqrt{Var(\hat{\beta}_j)}$$

### 9.1 Components Explained

- **$\sigma^2$:**
  - Represents data noise.
  - Can be reduced by including more relevant variables.

- **$SST_j$:**
  - Larger $SST_j$ reduces variance.
  - Increases with sample size.

- **$R_j^2$:**
  - Higher $R_j^2$ (multicollinearity) increases variance.
  - **Note:** Perfect multicollinearity ($R_j^2 = 1$) is disallowed.

## 10. Key Takeaways

- **OLS** estimates linear relationships between variables under specific assumptions.
- **Multiple Regression** allows control of multiple factors, enhancing causal inference.
- **Goodness of Fit ($R^2$):** Indicates the proportion of variance explained but doesn't imply causality.
- **Assumptions:** Critical for unbiased and efficient estimates; violations can lead to biased or inconsistent results.
- **Omitted Variable Bias:** Highlights the importance of including all relevant variables to avoid biased estimates.
- **Variance and Standard Errors:** Essential for hypothesis testing and constructing confidence intervals.
