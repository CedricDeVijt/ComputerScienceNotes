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

## 7.8: Formal Verification in Practice
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