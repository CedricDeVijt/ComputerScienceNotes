## 9.1 Introduction to Scoring Models

### Key Concepts:

- **Scoring Models** are mathematical models that assign scores to data points.
- The model predicts probabilities for different outcomes.
- Example setup:
  - Attributes: **A**, **B**
  - Outcome/Class: **C** ($+$ or $-$)

## 9.2 Maximum Likelihood

### Assumptions:

- **Independent and Identically Distributed (i.i.d.) Data:** Each tuple in the database is independent and follows the same distribution.
- **Uniform Model Prior:** All models are equally likely before observing data.

### Goal:

Maximize the likelihood function:

$$
L(M) = \prod_{i} P(data_i | M)
$$

#### Issues:

- For large datasets, the product becomes **numerically unstable**.
- Solution: Use the **log-likelihood**:
  $$
  \log L(M) = \sum_{i} \log P(data_i | M)
  $$

### Steps to Find the Maximum Likelihood Model:

1. Fix a model class.
2. Search for the model within the class that maximizes likelihood.

## 9.3 Analytical Solutions for Maximum Likelihood

### Analytical vs. Computational Solutions:

- Some models allow **analytical solutions** (e.g., Bayesian models).
- Others require solving an **optimization problem**.

### Example: Naïve Bayesian Model

- Dataset **D**.
- Find parameters (**a+**, **a-**, **b+**, **b-**, **c**) that maximize likelihood.

#### Derivation:

1. Compute **log-likelihood**: $L*$
2. Take partial derivatives w.r.t. parameters.
3. Solve for zeros to find maxima.

## 9.4 Connection to Naïve Bayes Classifier

### Key Insight:

- The maximum likelihood model corresponds to the model used by the **Naïve Bayes classifier**.
- This connection underpins the effectiveness of Naïve Bayes in classification tasks.

## Key Points to Remember

- **Likelihood Function:** Measures how well the model explains the data.
- **Log-Likelihood:** Simplifies calculations and avoids numerical instability.
- **Maximum Likelihood Estimation (MLE):** Seeks the parameter values that maximize the likelihood.
- **i.i.d. Assumption:** Key for MLE; ensures independence and uniformity in data.
- **Naïve Bayes Classifier:** Directly linked to the maximum likelihood model.
- **Parameter Estimation:** Analytical solutions exist for simple models; complex models may require optimization algorithms.
