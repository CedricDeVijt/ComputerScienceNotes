## 7.1 Particle Filtering

### Overview

- **Purpose**: Approximates solutions for problems where state space \(|X|\) is too large or continuous to use exact inference.
- **Key Idea**: Tracks a sample of states (called **particles**) instead of a full probability distribution.
- **Advantages**:
  - Memory efficient: List of particles replaces state probabilities.
  - Time complexity per step is linear in the number of samples.
- **Trade-Off**: Requires a large number of particles for accuracy.

### Process

1. **Representation**:
   - Use $N$ particles to approximate $P(X)$.
   - Probability $P(x)$ is proportional to the number of particles with value $x$.
2. **Elapse Time**:
   - Each particle transitions to a new position sampled from the **transition model**.
   - Reflects probabilities of state changes over time.
3. **Observation**:
   - Particles are weighted based on evidence likelihood, $P(e|x)$.
   - Weights are proportional but not normalized.
4. **Resampling**:
   - Particles are resampled based on weights to normalize distributions.
   - Ensures high-weight samples are prioritized.

## 7.2 Applications of Particle Filtering

### **Robot Localization**

- **Problem**: Locating a robot within a known map using sensor readings (e.g., sonar or laser).
- **Challenge**: Continuous state space prohibits storing full distributions.
- **Solution**: Particle filtering is used to approximate position probabilities.

### **Simultaneous Localization and Mapping (SLAM)**

- **Problem**: Simultaneously estimate both the map and the robot's location.
- **State Space**: Combines robot position and map details.
- **Techniques**:
  - Particle methods
  - Kalman filtering (for Gaussian HMMs)

## 7.3 HMM Queries and Algorithms

### Most Likely Explanation

- **Query**: Find the sequence of states with the highest joint probability given observations.
- **Algorithm**: Viterbi algorithm
  - Uses a **state trellis**, where:
    - Nodes represent states over time.
    - Arcs (transitions) have weights (probabilities).
    - Maximum-weight paths represent the most probable sequences.

### Forward vs. Viterbi Algorithms

- **Forward Algorithm**:
  - Calculates the sum of probabilities over all paths for evidence sequences.
- **Viterbi Algorithm**:
  - Identifies the single most probable sequence of states.

## 7.4 Dynamic Bayes Nets (DBNs)

### Overview

- **Purpose**: Generalization of HMMs to track multiple variables over time.
- **Structure**:
  - Repeated Bayesian network structure across time steps.
  - $t$-th step depends on $(t-1)$-th step.

### Exact Inference

1. **Procedure**:
   - Unroll the network for $T$ steps.
   - Apply variable elimination to compute $P(X_T|e_{1:T})$.
2. **Online Belief Updates**:
   - Eliminate past time-step variables.
   - Store current factors only.

### Particle Filters in DBNs

- A **particle** represents a complete state sample at a time step.
- Process:
  1. **Initialize**: Generate prior samples.
  2. **Elapse Time**: Sample successors for particles.
  3. **Observe**: Weight particles based on evidence likelihood.
  4. **Resample**: Draw samples based on updated weights.

---

## Key Points to Remember

- **Particle Filtering**:
  - Tracks samples (particles) to approximate state distributions.
  - Key steps: Transition (elapse time), weighting (observation), resampling.
- **Robot Localization**:
  - Employs particle filtering for continuous state spaces.
- **SLAM**:
  - Combines map building and localization using particle/Kalman methods.
- **Viterbi Algorithm**:
  - Determines the most probable sequence of states.
- **Dynamic Bayes Nets**:
  - Extends HMMs to model multiple interacting variables over time.
  - Particle filtering adapts to DBNs with sampling and weighting mechanisms.
