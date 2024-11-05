## 7.1: Introduction to Formal Specifications
### What is Formal Specification?
- **Formal Specification** is a rigorous mathematical approach to defining software systems, ensuring correctness and reliability.
- **When to Use**: Often used in critical systems where reliability is paramount (e.g., embedded systems, standards, high-risk software).
- **Why to Use**:
  - Ensures clarity and unambiguity.
  - Serves as a basis for testing and formal verification, especially in safety-critical software.
### Types of Specifications
1. **Informal**: Described in natural language; prone to ambiguity.
2. **Semi-formal**: Uses notations with syntax (e.g., UML diagrams), but lacks strict semantics.
3. **Formal**: Uses formal languages with well-defined syntax and semantics, allowing for mathematical proofs of correctness.

## 7.2: Design by Contract and Testing
### Key Concepts
- **Design by Contract**: Defines pre- and postconditions that must be true before and after method executions.
- **Testing with Formal Specifications**:
  - **Black-Box Testing**: Tests the system’s adherence to specifications without knowing its internals.
  - **Assertions**: Include logic assertions (e.g., invariants) within code for verification.
### Example: Binary Search
- **Precondition**: Array is sorted.
- **Postcondition**: Found element satisfies specified criteria or proves the element's absence.

## 7.3: Input/Output Specifications
### Preconditions and Postconditions
- **Preconditions**: Statements that must hold true before executing a procedure.
- **Postconditions**: Expected state after procedure completion. 
### Proving Correctness
- Ensures that given the preconditions, the postconditions will always be met, guaranteeing **partial** or **total correctness**.

## 7.4: State-Based Specifications
### Statecharts
- **State**: Defined as a condition met by the object, observable from the outside.
- **Transition**: A state change triggered by events, conditions, or time.
### Creating Test Cases from Statecharts
- **Coverage**: Ensure all transitions are tested at least once.
- **Consistency**: Verify that each event-state pair has a unique outcome.

## 7.5: Hoare Logic and the Weakest Precondition
### Hoare Triples
- **Format**: `{P} S {Q}`, where:
  - `{P}`: Precondition before executing `S`.
  - `{Q}`: Postcondition after executing `S`.
### Weakest Precondition
- **Weakest Precondition (WP)**: The minimal set of conditions required for postconditions to hold after execution of `S`.
- **Example Calculation**: For assignment, replace variable in `Q` with expression assigned to it in `S`.

## 7.6: Loop Invariants and Variants
### Loop Correctness
1. **Loop Invariant**: Condition that remains true at each iteration.
2. **Loop Variant**: A value that decreases with each loop, ensuring termination.
### Example
- Loop invariant is used to establish correctness.
- Loop variant helps in proving total correctness by guaranteeing the loop’s end.

## 7.7: Automated Theorem Provers and Tools
### Examples of Tools
- **Dafny**: Proves program correctness by verifying that postconditions always follow from preconditions.
- **VeriFast**: Verifies partial correctness of programs.

## 7.8: State-Based Specifications
### Introduction to State-Based Specifications
- **State-Based Specification** describes the sequence of states a system undergoes in response to external events.
- **Finite State Machines (FSMs)**: Commonly used to model systems that transition between different states based on specific inputs or conditions.
### Statecharts
- **Definition**: A visual representation of the system’s possible states and transitions between them. Widely used in UML and real-time systems.
- **Structure**:
  - **State**: A particular condition or mode of the system.
  - **Transition**: Change from one state to another, often triggered by an event or condition.
#### Example: Stack Statechart
- **Initial State**: Empty stack.
- **Transitions**:
  - `push()`: Changes state from empty to loaded.
  - `pop()`: If in loaded state, removes an element and may transition back to empty.
  - **Error Handling**: Calling `pop()` on an empty stack results in an error.
### Guards and Nested States
- **Guards**: Conditions that must be true for a transition to occur. They are used to make transitions **deterministic**.
  - **Example**: In a statechart of a stack, a `pop()` function might have different transitions based on the stack’s size (`size() > 1` or `size() = 1`).
- **Nested States**: States that contain sub-states, allowing for more detailed specification.
  - **Example**: A "loaded" stack state can have nested states like "loaded with one item" and "loaded with multiple items."
### Completeness, Consistency, and Unambiguity
- **Complete**: Every possible event/state pair has a defined transition.
  - **Verification**: Create a table with states as rows and events (with guards) as columns to check if each cell has a target state.
- **Consistent**: Every state must be reachable from the initial state, and the final state must be reachable from any other state.
  - **Verification**: Use a breadth-first spanning tree where the root is the initial state, ensuring all nodes eventually lead to a terminal state.
- **Unambiguous (Deterministic)**: Each event (including guards) should only appear on one transition per state.
  - **Verification**: Check the state-event table to confirm that no event has multiple transitions from the same state.
### Deduction of Test Cases from Statecharts
- **Test Case Design**:
  - **Coverage of Transitions**: Ensure all state transitions are tested at least once.
  - **Predicate for Each State**: Define predicates that can verify if the system is in each specific state.
  - **Breadth-First Spanning Tree Coverage**: Use the same table created for completeness to construct test cases.
  - **Stronger Coverage Options**:
    - Test all sequences of state transitions up to length `n`.
    - Force all guard conditions, including boundary values.

## 7.9: Formal Verification in Practice
### Practical Applications of Formal Verification
- **Use in High-Assurance Systems**:
  - **Example**: Secure air vehicle software relies on formal verification to ensure safety-critical properties.
- **Verification Techniques**:
  - **Modeling with Theorem Provers**: Create lightweight models of code and specifications to detect mismatches and inconsistencies.
  - **Automated Reasoning Tools**: Use tools like theorem provers to validate that specifications match implemented behaviors.
### Examples of Formal Verification Tools
- **Dafny**: Verifies that code satisfies preconditions and postconditions.
- **VeriFast**: Validates partial correctness, especially useful for security properties in complex systems.
### Importance of Formal Verification
- **Provable Security**: Ensures that critical security properties are met before deployment.
- **Bug Detection**: Identifies potential faults in code that could lead to vulnerabilities.
  - **Case Study**: Verification of Java/C++ code detected over 270 bugs in system drivers.
### Key Concepts in Formal Verification
- **Correctness**: Verifying if a system meets its specifications accurately.
  - **Partial Correctness**: If the function terminates, it does so according to specifications.
  - **Total Correctness**: Ensures both termination and correctness.
- **Traceability**: Ensures traceable connections between requirements and the system design, supporting maintenance and updates.

## 7.10: Formal Verification in Practice
### Real-World Applications
- Applied in high-assurance environments like **air vehicle software** and **Java/C++ code verification** to uncover errors in specifications and code.
### Formal Verification Benefits
- Provides provable security, which is essential in critical systems.
- Detects mismatches between code and specifications early in the cycle.

---

# Key Points to Remember

- **Formal Specification** is essential in safety-critical applications where reliability is non-negotiable.
- **Design by Contract**: Defines system expectations using preconditions and postconditions.
- **State-Based Specifications**: Useful for defining acceptable sequences of operations; essential in complex systems like traffic lights and drone management.
- **Hoare Logic**: Utilizes preconditions and postconditions to prove program correctness.
- **Weakest Precondition**: Helps in determining minimal conditions required for correctness.
- **Loop Invariants and Variants**: Ensure loop correctness and termination.
- **Automated Theorem Provers** like **Dafny** and **VeriFast** aid in verifying the adherence of code to its formal specifications.
- **Formal Verification in Practice** demonstrates its value in industries requiring high security, e.g., aviation and healthcare.