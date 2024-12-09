## 9.1: Introduction to Neural Networks

### Definition

- A **perceptron** is a simplified model of a biological neuron.
- Components:
  - Inputs (e.g., from sensors or other neurons)
  - Weights for each input
  - Activation function

### Key Concepts

- If the total weighted input exceeds a threshold, the neuron spikes.
- Human brain has ~86 billion neurons.

## 9.2: Perceptron

### Perceptron Basics

- **Functionality**:
  - Takes inputs and computes output based on weights and an activation function.
  - Example function: $f(x) = 1$ if $wx + b > 0$, otherwise $f(x) = 0$.

### Perceptron Learning Algorithm

1. Initialize weights randomly.
2. Iterate until convergence:
   - For each training example, adjust weights to improve prediction.
   - Example dataset:
     ```
     x1 x2 y
     1  3  0
     4  2  1
     ```

## 9.3: Learning as Optimization

### Loss Functions

1. **Quadratic Loss**:
   $L = \frac{1}{2}(h(x) - y)^2$
2. **Cross-Entropy Loss**:
   $L = -[y \log(h(x)) + (1-y) \log(1-h(x))]$

### Gradient Descent

- Update weights using:
  $w = w - \alpha \nabla_w J$
- **Epoch**: One complete iteration over the dataset.

## 9.4: Multi-Layer Perceptrons (MLPs)

### Structure

- Combines multiple perceptrons with **hidden layers**.
- Hidden layers act as space partitioners, enabling complex mappings.

### Optimization

- Use **backpropagation**:
  1. Forward pass: Compute outputs.
  2. Backward pass: Compute gradients and update weights.

## 9.5: Deep Neural Networks (DNNs)

### Key Features

- Learn large, complex mappings.
- Require significant data and computational power.

### Hyperparameters

1. Network structure
2. Learning rate
3. Activation function
4. Loss function

### Activation Functions

1. **Sigmoid**: $\sigma(x) = \frac{1}{1 + e^{-x}}$
2. **ReLU**: $f(x) = \max(0, x)$
3. **Softmax**: Normalizes outputs for multi-class classification.

## 9.6: Convolutional Neural Networks (CNNs)

### Basics

- Used for image classification.
- Instead of full connections, uses small **kernels** to scan inputs spatially.

### Advantages

- Fewer parameters to optimize.
- Efficient and less prone to overfitting.

### Applications

- Examples: **AlexNet (2012)**, **ResNet (2015)**

## 9.7: Overfitting and Regularization

### Causes

- Too many parameters relative to data.

### Solutions

1. **Regularization**: Add penalty to loss function.
2. **Dropout layers**: Randomly disable connections.
3. **Data augmentation**: Create new data samples (e.g., rotate images).

## 9.8: Conclusion

### Benefits of Neural Networks

- Universal Function Approximators.
- Learn complex patterns with minimal feature engineering.

### Challenges

- High data and computational requirements.

---

## Key Points to Remember

- **Perceptron**: Foundation of neural networks.
- **Loss functions**: Define model optimization goals.
- **Gradient descent**: Core of learning algorithms.
- **DNNs and CNNs**: Key architectures for different problems.
- **Overfitting**: Mitigated with regularization and data augmentation.
- **Activation functions**: Choose based on task.
