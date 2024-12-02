## 6.1 Introduction to Hidden Markov Models (HMMs)
### Overview
- **Hidden Markov Models (HMMs)** help in reasoning with **uncertainty over time**.
- **States** are unobserved (hidden), and observations are made indirectly.
- HMMs use a **Markov chain** where each state depends only on the previous state, and outputs are generated based on these states.
### Example Scenarios
- **Weather Prediction**: Observing umbrellas to infer weather states (rainy or sunny).
- **Ghostbusters Game**: Estimating ghost positions using noisy sensors.

## 6.2 Components of an HMM
### Key Components
1. **Initial State Distribution** (`P(X1)`)
2. **Transition Model** (`P(Xt | Xt-1)`): Probabilities for moving between states.
3. **Emission Model** (`P(E | X)`): Probabilities of observed evidence given the hidden state.

### Important Properties
- **Conditional Independence**:
  - Future states depend on the past only via the present state.
  - Current observation is independent of other variables given the current state.

## 6.3 Real-world Applications of HMMs
### Applications
- **Speech Recognition**: Acoustic signals as observations, words as states.
- **Machine Translation**: Observed words are translated based on latent linguistic structures.
- **Robot Tracking**: Using sensor readings to infer location.

## 6.4 Inference in HMMs
### Filtering / Monitoring
- **Objective**: Track the distribution of the current state (`Bt(X)`) given evidence up to time `t`.
- **Process**: 
  - Start with an initial belief, often uniform.
  - Update the belief over time and with new observations.

### Key Inference Algorithms
1. **Kalman Filter**: For continuous spaces and linear-Gaussian models.
   - Compactly represents belief with **mean** and **covariance matrix**.
   - Used in applications like **robot localization** and **trajectory estimation**.

## 6.5 Core HMM Algorithms
### Passage of Time
- **Belief Update**: Beliefs propagate forward over time, leading to increasing uncertainty.

### Observation Update
- **Belief Reweighting**: Beliefs are adjusted by the likelihood of new evidence, reducing uncertainty.

### The Forward Algorithm
- Combines both passage of time and observation updates to maintain **current belief** efficiently without normalization at each step.

## 6.6 The Kalman Filter
### Overview of Kalman Filters
- Extends HMMs to **continuous state spaces**.
- **Gaussian multi-variate distribution** is used to compactly represent belief (mean and covariance).

### Kalman Filter Properties
- Belief remains Gaussian if **transition and observation models** are linear-Gaussian.
- Kalman Gain matrix (`K`) adjusts belief based on observed evidence and prediction errors.

### Example: Kalman Filter in Rocket Tracking
- **State Update**: Position prediction with added Gaussian noise.
- **Observation Update**: Measured position with Gaussian error, refining the position estimate.

---

## Key Points to Remember

- **HMM Components**: Initial distribution, transition model, emission model.
- **Conditional Independence**: Observations depend on current state, not past/future directly.
- **Filtering**: The process of updating beliefs over time as new observations come in.
- **Forward Algorithm**: Efficient belief updating without normalization at each step.
- **Kalman Filter**: Handles continuous spaces, maintaining Gaussian distributions under linear-Gaussian assumptions.
