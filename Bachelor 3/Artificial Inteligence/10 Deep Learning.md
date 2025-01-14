## 10.1 Perceptrons

### Definition and Function

- **Perceptron**: A simplified model of a biological neuron.
  - Receives **input** from sensors or other neurons.
  - Emits a signal (spike) if the total input exceeds a **threshold**.
- **Components**:
  - **Inputs** $x_1, x_2, \ldots, x_n$
  - **Weights** $w_1, w_2, \ldots, w_n$
  - **Bias** $b$
  - **Activation Function**

#### Perceptron Formula

$$y = \text{Activation}(\sum\_{i=1}^{n} w_i \cdot x_i + b)$$

#### Activation Function Examples

- Step function.
- Sigmoid or ReLU for extended applications.

### Examples

- Changing weights $w$ and bias $b$ alters the function a perceptron computes.
  - E.g., $w_1 = 1, w_2 = -1, b = 0$ maps inputs $(x_1, x_2)$ to a binary decision.

### Learning Algorithm

1. **Objective**: Find weights and biases that approximate the dataset.
2. **Steps**:
   - Start with random weights.
   - Adjust weights iteratively using training examples:
     $$w \leftarrow w + \Delta w$$
   - Stop when performance is "good enough."

## 10.2 Learning as Optimization

### Loss Functions

- Measure prediction quality.
- Examples:
  - **Quadratic Loss**: $L = \frac{1}{2}(h(x) - y)^2$
  - **Cross-Entropy**: $L = -[y \log(h(x)) + (1-y) \log(1-h(x))]$

### Risk and Empirical Risk

- **Risk ($R(h)$)**: Expected loss across all possible inputs.
- **Empirical Risk ($R\_{emp}(h)$)**: Average loss over a finite test dataset.

### Gradient Descent

- Optimize weights $w$ to minimize loss:
  - Compute gradients $\nabla J$.
  - Update weights iteratively:
    $$w \leftarrow w - \alpha \nabla J$$
  - **Learning Rate ($\alpha$)**: Controls step size.
- Training with **batches** improves efficiency.
  - One complete pass over the dataset = **epoch**.

## 10.3 Multi-layer Perceptrons

### Structure

- Consists of:
  - Input layer.
  - One or more **hidden layers**.
  - Output layer.
- **Hidden Layer Role**: Partitions input space into more manageable regions.

### Training

- Uses **backpropagation**:
  - Compute error at the output layer.
  - Propagate error back to earlier layers.
  - Update weights using gradients from all layers.

## 10.4 Deep Neural Networks

### Hyperparameters

- **Network Structure**: Number of layers and neurons per layer.
- **Learning Rate ($\alpha$)**.
- **Activation Functions**:
  - Sigmoid: Outputs between $[0, 1]$.
  - ReLU: $\text{max}(0, x)$.

#### Softmax for Multi-class Classification

$$\text{Softmax}(z_i) = \frac{e^{z_i}}{\sum_j e^{z_j}}$$
Ensures output probabilities sum to 1.

### Universal Function Approximation

- **Theorem**: A sufficiently large two-layer NN can approximate any continuous function.
- Practical issues:
  - Risk of overfitting.
  - Requires early stopping or regularization.

## 10.5 Convolutional Neural Networks

### Structure and Advantages

- **Key Difference**: Uses **kernels** to connect layers.
  - Reduces number of parameters.
  - Increases spatial awareness.

### Applications

- **Image Recognition**:
  - Kernel slides over the image to extract features.
  - **Advantages over traditional NNs**:
    - Fewer weights.
    - Reduced computational cost.

---

## Key Points to Remember

- **Perceptrons**:
  - Simplest neural model.
  - Basis for more complex networks.
- **Learning**:
  - Optimization via gradient descent.
  - Loss functions determine training goals.
- **Deep Learning**:
  - Requires large datasets and computational resources.
  - Benefits include minimal feature engineering.
- **Convolutional Neural Networks**:
  - Efficient for spatial data like images.
  - Reduce overfitting with fewer parameters.
- **Activation Functions**:
  - Sigmoid for bounded outputs.
  - ReLU for internal layers to mitigate vanishing gradients.
- **Softmax**: Essential for multi-class classification.
