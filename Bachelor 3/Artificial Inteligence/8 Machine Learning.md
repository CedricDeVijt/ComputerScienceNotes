## 8.1: Basics of Machine Learning
### Key Concepts:
- **Machine Learning Goals**:
  - Learn models from data/experience.
  - Use models for optimal decision-making.
- Types of learning:
  - **Parameter learning**: Estimating probabilities.
  - **Structure learning**: Discovering dependencies (e.g., Bayesian Networks).
  - **Hidden concepts**: Clustering and neural networks.

### Applications:
1. **Spam Filtering**:
   - Input: Email
   - Output: Spam or Ham
   - Features: Keywords, patterns, sender information.
2. **Digit Recognition**:
   - Input: Pixel grids (images).
   - Output: Digits (0-9).
   - Features: Pixel values, shape patterns.
3. **Other Classification Tasks**:
   - Medical diagnosis, fraud detection, essay grading.

## 8.2: Model-Based Classification
### Naïve Bayes:
- Assumes features are independent given the label.
- **Key Steps**:
  - Compute posterior distribution $P(Y|F_1,...,F_n)$.
  - Use the formula: $P(Y|X) = \frac{P(X|Y)P(Y)}{P(X)}$.
### Strengths:
- Simple, scalable.
- Often works well even with simplifying assumptions.
### Weaknesses:
- Assumes independence between features.

## 8.3: Training and Testing
### Principles:
1. **Empirical Risk Minimization**:
   - Aim: Minimize loss on training data to approximate true distribution.
   - Risks: Overfitting (when the model memorizes rather than generalizes).

2. **Experimentation Cycle**:
   - Train on **training set**.
   - Tune using **held-out set**.
   - Evaluate on **test set**.

3. **Evaluation Metrics**:
   - Accuracy: Fraction of correctly classified instances.

## 8.4: Overfitting and Generalization
### Overfitting:
- Definition: Model fits training data too closely, failing on unseen data.
- Causes:
  - High model complexity.
  - Insufficient training data.
### Solutions:
1. **Regularization**:
   - Penalize overly complex models.
2. **Smoothing**:
   - Techniques like **Laplace smoothing** adjust probabilities for unseen events.

## 8.5: Decision Trees
### Key Concepts:
- **Tree Structure**:
  - Nodes represent decisions.
  - Leaves represent outcomes.
- **Hunt’s Algorithm**:
  - Splits data until all tuples have the same label.
### Steps:
1. **Split Criterion**: Optimize impurity measures (e.g., GINI index).
2. **Stopping Criteria**:
   - Nodes are pure (homogeneous class distribution).
   - Minimum number of data points at a node.
### Example:
- **GINI Index**: Measures impurity; lower values indicate purer nodes.

## 8.6: Advanced Decision Tree Techniques
### **Node Impurity Measures**
- **Gini Index**: Measures the impurity of a node:
  $GINI(t) = 1 - \sum_{j} p(j|t)^2$
  - Maximum impurity: $1 - \frac{1}{n_c}$ (when classes are equally distributed).
  - Minimum impurity: $0$ (when all records belong to a single class).
- **Entropy**: Evaluates the randomness in class distribution.
- **Misclassification Error**: Measures the proportion of incorrect classifications.

### **Splitting Criteria**
- For **Nominal Attributes**:
  - **Multi-way Split**: Partition data into subsets based on all unique attribute values.
  - **Binary Split**: Group attribute values into two subsets to minimize impurity.
- For **Numerical Attributes**:
  - Determine split points (e.g., $A < a$).
  - Efficient computation: Sort and sweep through potential split points (complexity $O(n \log n)$).

### **Stopping Criteria**
- Stop tree growth when:
  - All instances in a node belong to the same class.
  - Impurity measures do not improve with further splits.
  - A predefined minimum number of instances per node is reached.

## 8.7: Handling Overfitting in Decision Trees
### **Overfitting Concerns**
- Results in complex trees that fit training data but fail to generalize.
- Causes:
  - Noise in the data.
  - Lack of regularization or pruning.

### **Techniques to Address Overfitting**
1. **Pre-Pruning (Early Stopping)**:
   - Stop tree growth based on restrictive conditions:
     - All instances in a node have the same class.
     - Attribute values do not further refine the split.
     - Minimum number of data points reached.
2. **Post-Pruning**:
   - Grow the tree fully, then prune unnecessary nodes:
     - Use a validation set to assess the impact of pruning on generalization.
     - Replace sub-trees with leaf nodes based on majority class.

## 8.8: Logistic Regression
### **Core Concept**
- Logistic regression models the probability of a binary outcome as a linear function:
  $logit(p) = \ln \left( \frac{p}{1-p} \right) = w^T x + b$
  - $p$: Probability of the positive class.
  - $w$: Coefficients (weights).
  - $x$: Features.

### **Interpretation**
- Coefficients $w_i$ indicate the change in the odds ratio for a unit change in $x_i$:
  $Odds = \exp(w_i)$
- Example:
  - $P[Y=1|X] = \sigma(0.067 \cdot \text{Age} + 0.21 \cdot \text{BMI} - 15.23)$
  - A one-unit increase in BMI multiplies the odds of $Y=1$ by $e^{0.21} \approx 1.23$.

### **Training the Model**
- Use **maximum likelihood estimation**:
  $\text{Maximize: } P_M(Y|X)$
- Often solved via **gradient descent**:
  - Update rule: $w = w - \alpha \nabla J(w)$ (where $\alpha$ is the learning rate).

### **Regularization**
- Add regularization terms to prevent overfitting:
  - Ridge Regression ($L_2$): Penalizes $\sum w_i^2$.
  - LASSO ($L_1$): Penalizes $\sum |w_i|$.


## Key Points to Remember
#### Advanced Decision Tree Techniques
- **Impurity Measures**: Gini Index, Entropy, and Misclassification Error help decide splits.
- **Splitting**: Multi-way and binary splits optimize based on impurity for nominal and numerical attributes.
- **Stopping Criteria**: Stop if further splits don’t improve impurity or meet minimum data thresholds.
- **Overfitting Solutions**: 
  - **Pre-pruning**: Stop growth early.
  - **Post-pruning**: Fully grow and then prune using validation sets.
#### Logistic Regression
- **Model**: Predicts binary outcomes using the logistic function $logit(p) = w^T x + b$.
- **Odds Ratio**: Coefficients show how odds change for a unit increase in features.
- **Training**: Use maximum likelihood and optimize with gradient descent.
- **Regularization**: Prevent overfitting with Ridge ($L_2$) or LASSO ($L_1$) penalties.
