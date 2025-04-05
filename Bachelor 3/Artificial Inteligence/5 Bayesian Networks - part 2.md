## 5.1 Inference in Bayesian Networks

### Basic Inference

- **Goal**: Calculate $P(Q|E=e)$ where $Q$ is the query variable, $E$ is the evidence.
- **Normalization**: Transform joint probability $P(Q, E=e)$ into a conditional probability by normalizing.

### Efficient Inference Techniques

- **Variable Elimination**: Optimizes inference by eliminating unnecessary variables through re-arrangement.
- **Conditional Independence**: Uses the Bayes' Net structure to determine which variables are independent, simplifying calculations.

## 5.2 D-Separation and Independence in Bayesian Networks

### Concept of D-Separation

- **D-Separation**: A rule that determines when a set of variables is independent from another, given a third set of variables.
- **Path Activation**:
  - **Causal Chains**: Influence can be "blocked" by observing an intermediate variable.
  - **Common Cause**: Shared causes influence multiple variables.
  - **Common Effect (Collider)**: When two variables affect a third, observing the effect can link them.

## 5.3 Sampling Methods in Bayesian Networks

### Sampling Methods Overview

- Used when exact inference is complex; approximate results by generating samples.
- **Types of Sampling**:
  - **Prior Sampling**: Generates samples from the entire distribution.
  - **Rejection Sampling**: Rejects samples inconsistent with evidence.
  - **Likelihood Weighting**: Weights samples based on evidence.
  - **Gibbs Sampling**: Resamples variables iteratively to match evidence.

### Detailed Sampling Methods

- **Prior Sampling**: Draws samples based on prior probabilities.
- **Rejection Sampling**: Efficient when evidence is likely; ignores samples not matching evidence.
- **Likelihood Weighting**: Applies weights to samples based on evidence, making it suitable when evidence is unlikely.
- **Gibbs Sampling**: Adjusts samples iteratively for both upstream and downstream evidence.

## 5.4 Causality in Bayesian Networks

### Causality vs. Correlation

- **Bayesian Network Links**: Show **correlation**, not necessarily causation.
- **Causal Inference**: By adding causal assumptions, Bayes Nets can represent intervention outcomes.

### Backdoor Adjustment

- **Purpose**: Estimate the effect of actions by separating correlation from causation.
- **Method**: Adjust for potential confounders, enabling causal interpretation.

---

## Key Points to Remember

- **Inference**:

  - Use Bayes' Nets to calculate the probability of an outcome (query) given certain evidence.
  - Variable elimination and D-separation are crucial for optimizing inference.

- **D-Separation**:

  - **Causal Chains**, **Common Cause**, and **Common Effect** are configurations that affect independence.
  - Paths between variables can be **active** or **inactive** based on observed evidence.

- **Sampling**:

  - **Prior Sampling**: Sample directly from the distribution.
  - **Rejection Sampling**: Only keep samples that match evidence.
  - **Likelihood Weighting**: Assign weights to each sample based on evidence, improving accuracy.
  - **Gibbs Sampling**: Resamples while keeping evidence consistent, ideal for both upstream and downstream conditions.

- **Causal Inference**:
  - Bayesian Networks can represent causal relationships, allowing for intervention-based analysis.
  - **Backdoor Adjustment** corrects for confounding variables, isolating the effect of an intervention.
