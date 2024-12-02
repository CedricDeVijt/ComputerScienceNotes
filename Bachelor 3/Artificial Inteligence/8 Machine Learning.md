## 8.1 Introduction to Machine Learning
- **Machine Learning (ML)** focuses on acquiring models from data/experience rather than manual coding.
- Key areas in ML:
  - **Learning parameters** (e.g., probabilities).
  - **Learning structures** (e.g., Bayesian Networks).
  - **Learning hidden concepts** (e.g., neural networks, clustering).
- Primary topics:
  - Model-based classification: Naïve Bayes, Decision Trees, Logistic Regression.

## 8.2 Classification in Machine Learning
Classification involves predicting a **label** $y$ based on given inputs $x$. Applications include:
1. **Spam Filtering**: Using features like text patterns or sender information.
2. **Digit Recognition**: Analyzing image pixels to classify numbers.
3. Other tasks: Medical diagnosis, fraud detection, sentiment analysis, etc.

### Key Concepts
- **Features**: Attributes influencing decisions (e.g., pixel intensity, word frequency).
- Models predict **future labels** by learning from labeled datasets.

## 8.3 Model-Based Classification
- Models like **Naïve Bayes** assume conditional independence of features given a label.
- Key steps:
  1. Instantiate observed features.
  2. Compute **posterior probabilities** of labels using evidence.

## 8.4 Naïve Bayes Classifier
- Simplifies computation by assuming all features are independent effects of the class label.
- Example:
  - **Bag-of-words** model for text classification assumes word order is irrelevant.
- Parameters include **priors** $P(Y)$ and conditional probabilities $P(F|Y)$.

## 8.5 Overfitting and Generalization
- **Overfitting**: Model fits training data too closely but fails to generalize.
- Techniques to mitigate overfitting:
  - Use more data.
  - Apply **regularization** to penalize complexity.
  - Split data into **training**, **validation**, and **test sets**.

## 8.6 Decision Trees
- Decision Trees split data hierarchically based on feature values.
- **Entropy** and **Information Gain** measure the effectiveness of splits.
- Overfitting is controlled by:
  - **Pruning**: Removing less significant branches.
  - Limiting tree depth or splitting based on significance tests.

## 8.7 Logistic Regression
- **Logistic Regression** models the probability of binary outcomes using the **sigmoid function**.
- Assumes:
  - Log-odds ($\log(p/(1-p))$) are a linear function of input features.
- Optimization:
  - Parameters are learned by minimizing the **negative log-likelihood**.

### Key Equations
- **Sigmoid Function**:
  $P(Y=1|X) = \sigma(w^T x + b) = \frac{1}{1 + e^{-(w^T x + b)}}$

---

# Key Points to Remember
- **Features** are the foundation of classification models.
- **Naïve Bayes** assumes feature independence, making it computationally efficient.
- **Overfitting** is when a model memorizes training data rather than generalizing.
- **Entropy** quantifies uncertainty; **Information Gain** guides decision tree splits.
- **Logistic Regression** optimizes probabilities using the sigmoid function and gradient descent.
- Data splits:
  - Training: Learning parameters.
  - Validation: Tuning hyperparameters.
  - Testing: Evaluating performance.
