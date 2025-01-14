## 8.1: Basics of Machine Learning

### Key Concepts

- **Machine Learning Goals**:
  - Learn models from **data/experience**.
  - Use models for **optimal decision-making**.
- **Types of Learning**:
  - **Parameter learning**: Estimating probabilities.
  - **Structure learning**: Discovering dependencies (e.g., Bayesian Networks).
  - **Hidden concepts**: Clustering and neural networks.

### Applications

1. **Spam Filtering**:
   - **Input**: Email.
   - **Output**: Spam or Ham.
   - **Features**: Keywords, patterns, sender information.
2. **Digit Recognition**:
   - **Input**: Pixel grids (images).
   - **Output**: Digits (0-9).
   - **Features**: Pixel values, shape patterns.
3. **Other Classification Tasks**:
   - Examples: Medical diagnosis, fraud detection, essay grading.

## 8.2: Model-Based Classification

### Naïve Bayes

In a Naive Bayes classifier, the key formula is based on **Bayes' theorem** and the **naive assumption** that features $F_1, F_2, \dots, F_n$ are conditionally independent given the class $Y$. Let’s break it down:

#### Bayes' Theorem:

$$
P(Y|X) = \frac{P(X|Y)P(Y)}{P(X)},
$$

where:

- $P(Y|X)$: Posterior probability of class $Y$ given features $X$.
- $P(X|Y)$: Likelihood of features $X$ given class $Y$.
- $P(Y)$: Prior probability of class $Y$.
- $P(X)$: Evidence (normalizing constant, often ignored in classification since it is the same for all classes).

#### Naive Bayes Assumption:

The naive assumption states that the features $F_1, F_2, \dots, F_n$ are conditionally independent given $Y$. This simplifies the joint probability $P(X|Y)$ as:

$$
P(X|Y) = P(F_1, F_2, \dots, F_n | Y) = \prod_{i=1}^n P(F_i | Y).
$$

#### Combined Formula:

Substituting the naive assumption into Bayes' theorem, we get:

$$
P(Y|X) \propto P(Y) \prod_{i=1}^n P(F_i | Y),
$$

where $P(Y|X)$ is proportional to $P(Y) \prod_{i=1}^n P(F_i | Y)$ because $P(X)$ is constant across all classes.

#### Joint Probability:

The joint probability of $Y$ and all features is given by:

$$
P(Y, F_1, F_2, \dots, F_n) = P(Y) \prod_{i=1}^n P(F_i | Y).
$$

This formula is central to computing the posterior probabilities for classification tasks in the Naive Bayes framework.

### Strengths

- **Simple** and **scalable**.
- Works well even with simplifying assumptions.

### Weaknesses

- Assumes **independence between features**, which might not hold true.

## 8.3: Training and Testing

### Principles

1. **Empirical Risk Minimization**:

   - Minimize loss on **training data** to approximate the true distribution.
   - **Risk**: Overfitting when the model memorizes instead of generalizing.

2. **Experimentation Cycle**:

   - **Train** on training set.
   - **Tune** using a held-out set.
   - **Evaluate** on a test set.

3. **Evaluation Metric**:
   - **Accuracy**: Fraction of correctly classified instances.

## 8.4: Overfitting and Generalization

### Overfitting

- **Definition**: Model fits training data too closely, failing on unseen data.
- **Causes**:
  - High model complexity.
  - Insufficient training data.

### Solutions

1. **Regularization**:
   - Penalize overly complex models.
2. **Smoothing**:
   - Adjust probabilities for unseen events using techniques like **Laplace smoothing**.

## 8.5: Decision Trees

### Key Concepts

- **Tree Structure**:
  - **Nodes** represent decisions.
  - **Leaves** represent outcomes.
- **Hunt’s Algorithm**:
  - Splits data until all tuples have the same label.

### Steps

1. **Split Criterion**:
   - Optimize impurity measures (e.g., **GINI index**).
2. **Stopping Criteria**:
   - Stop if:
     - Nodes are pure (homogeneous class distribution).
     - Minimum number of data points at a node is reached.

### Example: GINI Index

- Measures impurity:
  $$GINI(t) = 1 - \sum_{j} p(j|t)^2$$
  - **Maximum impurity**: $1 - \frac{1}{n_c}$ (equal class distribution).
  - **Minimum impurity**: $0$ (pure class).

## 8.6: Advanced Decision Tree Techniques

### Node Impurity Measures

1. **Gini Index**:
   - Formula: $GINI(t) = 1 - \sum_{j} p(j|t)^2$.
2. **Entropy**:
   - Evaluates randomness in class distribution.
3. **Misclassification Error**:
   - Measures the proportion of incorrect classifications.

### Splitting Criteria

- **For Nominal Attributes**:
  - **Multi-way Split**: Partition data based on unique attribute values.
  - **Binary Split**: Group attribute values into two subsets to minimize impurity.
- **For Numerical Attributes**:
  - Determine split points (e.g., $A < a$).
  - Efficient computation: Sort and sweep through potential split points (complexity $O(n \log n)$).

### Stopping Criteria

- Stop tree growth if:
  - All instances in a node belong to the same class.
  - Impurity measures do not improve with further splits.
  - A predefined **minimum number of instances** per node is reached.

## 8.7: Handling Overfitting in Decision Trees

### Overfitting Concerns

- **Causes**:
  - Noise in the data.
  - Lack of regularization or pruning.

### Techniques to Address Overfitting

1. **Pre-Pruning (Early Stopping)**:
   - Stop tree growth based on restrictive conditions:
     - All instances in a node have the same class.
     - Attribute values do not further refine the split.
     - Minimum number of data points reached.
2. **Post-Pruning**:
   - Fully grow the tree, then prune unnecessary nodes:
     - Use a **validation set** to assess pruning impact.
     - Replace sub-trees with leaf nodes based on the majority class.

## 8.8: Logistic Regression

### Core Concept

- Logistic regression models the probability of a binary outcome as a linear function:
  $$logit(p) = \ln \left( \frac{p}{1-p} \right) = w^T x + b$$
  - $p$: Probability of the positive class.
  - $w$: Coefficients (weights).
  - $x$: Features.

### Interpretation

- Coefficients $w_i$ indicate the change in the **odds ratio** for a unit change in $x_i$:
  $$Odds = \exp(w_i)$$
- Example:
  $$P[Y=1|X] = \sigma(0.067 \cdot \text{Age} + 0.21 \cdot \text{BMI} - 15.23)$$
  - A one-unit increase in BMI multiplies the odds of $Y=1$ by $e^{0.21} \approx 1.23$.

### Training the Model

- Use **maximum likelihood estimation**:
  $$\text{Maximize: } P_M(Y|X)$$
- Often solved via **gradient descent**:
  - Update rule: $w = w - \alpha \nabla J(w)$ (where $\alpha$ is the learning rate).

### Regularization

- Add regularization terms to prevent overfitting:
  - **Ridge Regression ($L_2$)**: Penalizes $\sum w_i^2$.
  - **LASSO ($L_1$)**: Penalizes $\sum |w_i|$.

---

## Key Points to Remember

- **Naïve Bayes**: Assumes feature independence; simple but powerful.
- **Overfitting**: Avoid by regularization, smoothing, pruning.
- **Decision Trees**: Utilize impurity measures (e.g., Gini, entropy) for splits; address overfitting with pre- and post-pruning.
- **Logistic Regression**: Models binary outcomes with interpretative coefficients; regularization improves generalization.
- **Training Cycle**: Train on training data, tune on validation data, and evaluate on test data.
