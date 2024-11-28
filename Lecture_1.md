# Lecture 1

## Steps of an econometric analysis
An empirical analysis uses data to test a theory or to estimate a relationship  
1. Careful formulation of the question of interest  
2. Formulation of an econometric model (on the basis of economic arguments)  
3. Hypotheses can be formulated in terms of unknown model parameters  
4. Data collection and use of econometric methods to estimate the parameters in the econometric model and formally test the hypotheses of interest

### Example
1. What is the effect of education on wages?
2. Economic model: schooling is an investment to maximize future outcomes. More education increases productivity which leads to higher wages:
$$
wage = f (education, other(unobserved)f actors)
$$
	Economic model: 
$$ \begin{aligned}
	y &= \beta_{0} + \beta_{1}x + u\\ 
	y &: \text{wage} \\ 
	x &: \text{education}\\
	u &: \text{unobserved factors}
\end{aligned} $$
3. Want to know unknown parameter $\beta_1$ (or maybe $\beta_0$) and test $\beta_1 = 0$
4. Sample of workers with varying $x$ and $y$; use econometric techniques to estimate $\beta_1$ and to evaluate precision of estimates

## Two estimation problems: Prediction vs causal inference
**Prediction:** 
Compares outcomes for different combinations of values of independent variables. 
> [!GOAL]
> The goal is to predict the dependent variable based on the observed values of independent variables.

**Causal inference:** 
Independent variables are regarded as causes of a change in the dependent variable. 
> [!GOAL]
> The goal is to determine whether a particular independent variable affects the dependent variable, and to estimate the magnitude of that effect.

## Discrete Random Variables
**Definition**: A discrete RV takes on a finite or countable number of values.
**Outcomes**: List of values $x_1, x_2, \dots, x_k$​ with associated probabilities $p_1, p_2, \dots, p_k$​.
**Properties:**
- Each probability $p_j = P(X = x_j)$ is between 0 and 1.
- Total probability: $p_1 + p_2 + \dots + p_k = 1$.

**PDF**: $f(x_j) = p_j$​; gives the probability of $X$ taking a specific value $x_j$.

## Continuous Random Variables
**Definition**: A random variable $X$ that can take any value in a continuous range (e.g., all real numbers $\mathbb{R}$).
**Properties**:
- Each specific value has zero probability; instead, probabilities are assigned to ranges.

**PDF**: Use the probability density function (PDF) to find the probability over a range $[a, b]$:
- $P(a \leq X \leq b)$ is the area under the PDF between $a$ and $b$.

**CDF**: The cumulative distribution function (CDF) $F(x) = P(X \leq x)$, giving the probability that $X$ is less than or equal to $x$.
**For Discrete RVs**: CDF sums probabilities for all values $x_j \leq x$.
#### PDF and CDF of a continuous RV
![[Pasted image 20241115041720.png]]
