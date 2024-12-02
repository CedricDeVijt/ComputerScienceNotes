## 4.1 Introduction to Bayes' Nets
### Motivating Example
- **Scenario**: A patient with asthma, elevated white blood cell count, elevated amylase levels, and normal body temperature. What is the probability they have a **Systemic Inflammation Reaction (SIR)**?
- **Purpose**: To model this problem using **Bayesian Networks** and make inferences about probable conditions based on observed evidence.

### Key Questions
1. How do we **model** knowledge about this patient?
2. How do we make **inferences** from this model?

## 4.2 Fundamentals of Probability
### Probability Notation
- **Random variables**: $X, Y, Z$
- **Joint probability distribution**: $P(X, Y, Z)$
- **Conditional probability**: $P(X|Y)$
- **Chain rule**: Used to break down joint distributions.

## 4.3 Independence in Probability
### Independence Concepts
- **X and Y are independent** $P(X, Y) = P(X)P(Y)$.
- **Product rule**: $P(x,y)=P(x|y)\cdot P(y)$
- **Conditional Independence**: X and Y are conditionally independent given Z if:
  $P(X, Y|Z) = P(X|Z)P(Y|Z)$
### Examples of Independence
- **Coin flips**: Each flip is independent.
- **Traffic and rain**: They may be dependent but can be modeled with conditional independence.

## 4.4 Introduction to Bayes' Nets
### Big Picture
- **Problem with full joint distributions**: Hard to estimate and manage when dealing with many variables.
- **Solution**: Bayes' nets, which use **local conditional probabilities** to describe complex joint distributions.
### Components of a Bayes' Net
- **Nodes**: Represent variables.
- **Edges**: Represent dependencies.
- **Conditional Probability Tables (CPTs)**: Represent the relationships between a node and its parents.

## 4.5 Example - The Alarm Network
- **Variables**: Burglary, Earthquake, Alarm, John calls, Mary calls.
- **Example CPT**:
  $P(Alarm|Burglary, Earthquake)$
  If both burglary and earthquake occur, the alarm rings with 95% probability.
  
![[Pasted image 20241115093229.png|400]]

## 4.6 Structure of Bayes' Nets
### Size and Complexity
- **Joint distribution over N Boolean variables**: Size = $2^N$
- **Bayesian net with up to k parents**: $O(N \times 2^{k+1})$
  - **Advantage**: Bayes’ nets require less space and are easier to calculate compared to full joint distributions.

## 4.7 Causality and Conditional Independence
### Causal Chains
- A chain such as $X \rightarrow Y \rightarrow Z$.
  - **Example**: Low pressure causes rain, which causes traffic.
  - **Conditional independence**: X is independent of Z given Y.

### Common Cause (Confounder)
- Two effects $X$ and $Z$ arise from a common cause $Y$.
  - Example: Project due causes both forums being busy and the lab being full.

### Common Effect (Collider)
- Two causes $X$ and $Y$ affect a common effect $Z$.
  - Example: Rain and a ballgame both lead to traffic.

## 4.8 D-Separation
### D-Separation Algorithm
- A method to determine whether two variables are **conditionally independent** given some evidence.
- **Active paths**: Pathways between variables that remain after accounting for evidence.
- **Inactive paths**: Blocked by observed variables, ensuring conditional independence.

![[bayes_ball.png|500]]

## 4.9 Inference in Bayes' Nets
### Inference by Enumeration
- **Naive approach**: Compute full joint distributions to make inferences.
- **Efficient approaches**: Reordering terms in calculations through techniques like **variable elimination** to reduce complexity.

---

# Key Points to Remember

- **Bayes' nets** provide a compact way to model joint distributions using local conditional dependencies.
- **Conditional independence** is the foundation of simplifying complex probabilistic models.
- **D-separation** helps identify conditional independence from the graph structure alone.
- **Causal relationships** are often simpler to represent with Bayes’ nets, but the networks do not always reflect causality (only conditional independence).
- **Inference methods** like enumeration and variable elimination are used to efficiently answer probability queries in Bayesian networks.