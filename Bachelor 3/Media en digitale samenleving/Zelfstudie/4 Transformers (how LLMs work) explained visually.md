## 4.1 Generative Pretrained Transformers (GPT) Overview

### Core Components of GPT

- **Generative**: Produces new text through sequential predictions
- **Pretrained**: Initialized with broad knowledge from massive datasets
- **Transformer**: Neural network architecture using attention mechanisms

### Text Generation Process

1. **Prediction-Sampling Loop**:
   - Takes initial text snippet
   - Predicts probability distribution for next token
   - Samples from distribution and appends result
   - Repeats process with updated text
2. **Scaling Effects**:
   - GPT-2 (smaller) produces less coherent text
   - GPT-3 (larger) generates context-aware narratives
   - Demonstrated through pi creature example in math-themed story

## 4.2 Transformer Architecture and Data Flow

### Tokenization Process

- Input broken into **tokens**:
  - Words/subwords for text
  - Image patches or sound chunks for multimedia
- GPT-3 vocabulary: 50,257 tokens

### Vector Encoding

- Each token mapped to high-dimensional vector (12,288D in GPT-3)
- **Embedding Matrix (We)**:
  - 617 million parameters in GPT-3
  - Learned semantic relationships between tokens

### Network Operations

1. **Attention Blocks**:
   - Enables contextual understanding through vector interactions
   - Resolves ambiguous meanings (e.g., "model" in ML vs fashion)
2. **Feed-Forward Layers**:
   - Parallel processing of individual vectors
   - Refines vector representations through learned transformations

## 4.3 Deep Learning Foundations

### Machine Learning Framework

- **Parameterized Models**: 175 billion tunable weights in GPT-3
- **Backpropagation**: Training algorithm enabling large-scale learning
- **Tensor Processing**: Data represented as multi-dimensional arrays

### Architectural Constraints

- Input/output must be numerical tensors
- Layer-by-layer transformation pipeline
- Weighted sums dominate computations (matrix multiplications)

## 4.4 Word Embeddings and Semantic Encoding

### Geometric Interpretation

- Words mapped to points in 12,288D space
- Semantic relationships emerge through vector positions:
  - Gender: woman - man $\approx$ queen - king
  - Nationality: Italy - Germany + Hitler $\approx$ Mussolini
  - Plurality: cats - cat direction encodes number

### Dot Product Analysis

- Measures vector alignment:
  - Positive = similar directions
  - Negative = opposing directions
  - Used in attention calculations and semantic tests

## 4.5 Context Processing and Limitations

### Context Window Mechanics

- Fixed sequence length (2048 tokens in GPT-3)
- Vectors update through network layers to absorb context
- Early chatbot limitations from context overflow

### Dynamic Meaning Construction

- Initial embeddings (static word meanings)
- Progressive refinement through attention/FFN layers
- Final vectors encode nuanced, context-aware representations

## 4.6 Prediction and Output Generation

### Unembedding Process

- **Unembedding Matrix (Wu)**: 617M parameters
- Maps final vector to token probabilities
- Simultaneous predictions across all context positions

### Probability Shaping

1. **Softmax Function**:
   - Converts logits to valid probability distribution
   - $softmax(z_i) = \frac{e^{z_i/T}}{\sum_j e^{z_j/T}}$
2. **Temperature Control**:
   - T > 1: More exploratory outputs
   - T < 1: More deterministic choices
   - T=0: Always select maximum probability token

## 4.7 Training and Model Scaling

### Parameter Efficiency

- Shared prediction across context positions
- Matrix-based weight organization (28k matrices in GPT-3)
- Embedding/Unembedding matrix symmetry

### Scaling Observations

- Emergent capabilities from size increases
- Performance jumps between GPT-2/GPT-3 demonstrate nonlinear scaling
- Current practical limits on context window retention

---

## Key Points to Remember

- Transformers process **sequences through attention** and feed-forward layers
- **Word embeddings** encode semantic relationships geometrically
- GPT's text generation uses **predict-sample-append** looping
- **Softmax with temperature** controls output randomness
- Model performance scales nonlinearly with parameter count
- **175 billion parameters** in GPT-3 enable complex reasoning
- **Context window limits** (2048 tokens) affect conversation continuity
- **Dot products** quantify semantic alignment between vectors
- Training through **backpropagation** adjusts embedding relationships
- **Matrix multiplications** form computational backbone
