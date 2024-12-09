## 11.1: Introduction to Refactoring

### What is Refactoring?

- **Definition**:
  - **Verb**: Process of changing a software system to improve internal structure without altering external behavior.
  - **Noun**: A behavior-preserving source-to-source program transformation.

### Why Refactoring?

- **Reasons**:
  - Adaptability for **new requirements**.
  - Correct mistakes in earlier stages to reduce maintenance costs (**Maintenance effort: 50%-75% of total costs**).
  - Address **Technical Debt**: Investing in adaptability to reduce long-term expenses.

### When to Refactor?

- **Indicators**:
  - Code smells (e.g., duplicated code, large classes, nested conditionals).
  - High maintenance cost due to inefficient design.

## 11.2: Key Refactoring Techniques

### Primitive Refactorings

- **Class Refactorings**: Add, rename, remove class.
- **Method Refactorings**: Add, rename, move, extract code into methods.
- **Attribute Refactorings**: Add, rename, remove attributes.

### Composite Refactorings

- Combine simple refactorings for larger structural improvements:
  - **Extract Superclass**
  - **Pull Up/Push Down** methods or attributes.

## 11.3: Refactoring in Action

### Example: Internet Banking System

![[Pasted image 20241203141606.png]]

#### Requirements:

- **Functional**:
  - Customers own accounts for deposits, withdrawals, transfers.
- **Non-functional**:
  - Secure: Only authorized users access accounts.
  - Reliable: Transactions maintain consistent state.

#### Class Diagram:

- **IBBank** manages accounts and transactions with methods for access and balance checks.
- Refactor methods like `get_balance` and `transfer` to include transaction protocols.

#### Expanding for Concurrent Access:

- Add attributes: `transactionId`, `workingBalance`.
- Add methods: `lock`, `commit`, `abort`, `isLocked`.

![[Pasted image 20241203141721.png]]

## 11.4: Supporting Tools and Best Practices

### Tool Support

- Refactoring should be **efficient and failure-proof**:
  - Regression testing ensures correctness.
  - Configuration management tracks changes and allows rollback.

### Iterative Development Lifecycle:

1. **Prototyping**: Implement initial functionality.
2. **Expansion**: Add features like concurrent access.
3. **Consolidation**: Optimize for reuse, address technical debt.

## 11.5: Identifying Code Smells

### Examples:

- **Duplicated Code**: Indicates potential for extracting methods.
- **Large Classes/Methods**: May require splitting into smaller components.
- **Abusive Inheritance**: Suggests inappropriate class relationships.

### Rule of Thumb:

- **DRY Principle**: “Don’t Repeat Yourself.”

## 11.6: Advanced Topics in Refactoring

### Refactoring and Technical Debt

- Refactoring reduces technical debt by addressing structural weaknesses early.

### Refactoring and Design by Contract:

- Contracts (preconditions, postconditions, invariants) ensure behavior preservation during refactoring.

## Key Points to Remember

- **Refactoring Definitions**:
  - Changing internal code structure without altering behavior.
  - Improves maintainability and adaptability.
- **When to Refactor**:
  - Code smells.
  - Increasing maintenance costs.
- **Core Techniques**:
  - Add, rename, move, and extract methods or classes.
  - Composite refactorings like Extract Superclass.
- **Practical Example**:
  - Internet Banking expanded for secure, concurrent transactions.
- **Key Tools**:
  - Regression testing.
  - Version management.
- **Best Practices**:
  - Consolidate after each expansion.
  - Use code smells as guides.
