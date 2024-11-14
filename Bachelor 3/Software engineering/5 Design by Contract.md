# 5.1: Introduction to Design by Contract

### What is Design by Contract?
Design by Contract (DbC) formalizes the relationship between components in software as a **contract**, where each party has obligations and benefits.

- **Client (caller)** has obligations (preconditions).
- **Supplier (called method)** guarantees benefits (postconditions).

### Key Concepts
- **Preconditions**: What must be true before a method is called.
- **Postconditions**: What must be true after the method completes.
- **Invariants**: Conditions that must always be true for a class.

### Benefits of DbC
- **Prevention over detection**: Avoiding defects rather than finding them through testing.
- Useful in **Object-Oriented Programming** for class interface validation.
- Example: The **Ariane 5 crash** could have been avoided using DbC.

# 5.2: Preconditions, Postconditions, and Invariants

### Preconditions
A contract's "promise" from the client. Example:
```java
precondition: {x >= 9}
```
If the precondition is false, the method shouldn't be called.

### Postconditions
The state guaranteed by the method after execution:
```java
postcondition: {x >= 13}
```

### Invariants
These are conditions that must remain true during the object's lifecycle, ensuring consistency.

# 5.3: Assertions and Redundant Checks

### Assertions
Assertions are boolean expressions that verify the correctness of code:
- Example: `assert(!this.isEmpty())`

They formalize **preconditions, postconditions, and invariants** in the code, helping maintain **documentation and correctness**.
### Redundant Checks
These should be avoided because:
- **Complexity**: Increases unnecessary checks.
- **Performance**: Slows down execution.
- **Responsibility**: Clients should satisfy preconditions, not the supplier.

# 5.4: Exception Handling

When an assertion fails, **exceptions** should be raised. Example:
```java
public char pop() throws AssertionException {
    assert(!this.isEmpty());
    return _store[_size--];
}
```
Using exceptions helps identify **violations** of preconditions or postconditions.

# 5.5: Design by Contract and Testing

- **Complementary**: DbC prevents certain types of errors, while **testing** detects errors after they occur.
- Use **DbC with black-box testing** (equivalence partitioning, boundary analysis).
- **Consumer-driven contract testing** is critical for microservices.

# 5.6: Subclassing, Subcontracting, and the Liskov Substitution Principle

### Subclassing and Contracts
- **Subclasses** must follow the parent's contract but can **strengthen** postconditions or **weaken** preconditions.

### Liskov Substitution Principle (LSP)
You can substitute a subclass for any of its superclasses **if**:
- Invariant: `{I’} = {I}`
- Precondition: `{P’} <= {P}`
- Postcondition: `{Q’} >= {Q}`

### Behavioral Subtyping
- A subtype must respect the contract of its supertype. For example, a **Square** cannot behave exactly like a **Rectangle** in all scenarios.

# 5.7: Modern Applications – REST API and Banking Example

### REST API Contracts
- **Consumer-driven contract testing** ensures that services work independently.
- Contracts define the relationship between microservices.

![[Pasted image 20241016121416.png]]

---
# Key Points to Remember

- **Design by Contract** establishes obligations (preconditions), benefits (postconditions), and consistency (invariants).
- **DbC vs. Testing**: DbC **prevents** errors, while testing **detects** them.
- **Assertions** ensure that contracts are verified during code execution.
- **Preconditions** can be weakened, and **postconditions** can be strengthened in subclasses to maintain contracts.
- Use DbC in combination with **black-box testing** techniques.
- **Consumer-driven contract testing** is essential for modern microservices architectures.
- The **Liskov Substitution Principle** ensures that subclassing respects contracts.