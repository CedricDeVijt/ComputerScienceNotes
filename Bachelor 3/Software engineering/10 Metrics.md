## 10.1: Introduction to Software Metrics

### Importance of Metrics

- **Why Metrics?**: You cannot control what you cannot measure (De Marco). Measurement quantifies concepts for understanding, control, and improvement.
- **When to Use Metrics?**:
  - **Effort Estimation**: Early in the lifecycle to predict production efforts.
  - **Quality Assessment**: Control attributes during development and compare/improve processes.

## 10.2: Fundamental Concepts in Metrics

### Measurement Theory

- **Definition**:
  - **Measure**: A function mapping an attribute to a symbolic representation.
  - **Metric**: A measure with range in real numbers satisfying mathematical properties.
- **Representation Condition**: Ensures empirical relations correspond to mathematical relations.

### Types of Measures

- **Direct Measures**: Directly observed (e.g., LOC, number of defects).
- **Indirect Measures**: Derived (e.g., defect density = defects / LOC).

### Scales of Measurement

- **Nominal**: Categorical (e.g., error types).
- **Ordinal**: Ordered categories (e.g., task complexity).
- **Interval**: Quantitative without a true zero (e.g., Celsius temperature).
- **Ratio**: Quantitative with a true zero (e.g., LOC, defect density).

## 10.3: Effort Estimation Techniques

### Techniques

1. **Expert Judgment**: Relies on experienced estimators.
2. **Analogical Estimation**: Based on comparisons with similar projects.
3. **Algorithmic Cost Modeling**: Uses formulas calibrated with historical data.
   - Example: **COCOMO Model**:
     - **Effort = C × (Size)^S**
     - Varies based on project complexity (Organic, Semi-Detached, Embedded).

### Putnam’s Model

- Effort and Time are interdependent.
- **Key Insight**: Increasing scheduled time can significantly improve productivity.

## 10.4: Product Size Metrics

### Lines of Code (LOC)

- **Advantages**: Tangible, easy to measure.
- **Disadvantages**:
  - Ignores software reuse and quality.
  - Highly dependent on programming language.

### Function Points (FP)

- Measures functionality based on:
  - Inputs, Outputs, User Interactions, Files, External Interfaces.
- **Advantages**: Language-independent, meaningful for data processing.
- **Disadvantages**: Requires subjective judgment.

### Use Case Points (UCP)

- Derived from actor and use case complexities.
- Includes adjustments for technical and environmental factors.

## 10.5: Quality Metrics

### ISO 9126 Model

- **Quality Attributes**: Functionality, Reliability, Efficiency, Usability, Maintainability, Portability.
- **Metrics Examples**:
  - Defect Density = Defects / Size.
  - Correction Time = Time to repair defects.

### Coupling and Cohesion Metrics

- **Coupling**: Number of classes required for a class to function.
- **Cohesion**: Degree to which methods within a class share data.

## 10.6: Advanced Topics

### Planning and Velocity

- **Story Points**: Estimation technique using relative effort.
- **Velocity**: Amount of work (in story points) completed per sprint.

### Challenges in Metrics Usage

- Misleading Data: Context matters (e.g., LOC differences between languages).
- Measurement Unreliability: False positives and negatives in internal metrics.

---

# Key Points to Remember

- **Effort Estimation**: Use a combination of expert judgment, analogy, and algorithmic models for accurate predictions.
- **Metric Validity**: Ensure metrics align with the representation condition.
- **Function Points**: Preferred for measuring functionality over LOC.
- **COCOMO Model**: Adapt effort based on project complexity (Organic, Semi-Detached, Embedded).
- **Quality Metrics**: ISO 9126 model provides a structured approach to assess software quality.
- **Challenges**: Avoid over-reliance on a single metric; always consider the context and combine multiple data sources.
