## 6.1 Introduction to Testing
### When to Test?
- Testing should begin **early** in the development process.
- Repeat testing towards the end to assess the **reliability** of the system.

![[Pasted image 20241023110234.png]]
### Why Test?
- Testing is essential for **risk reduction**.
- The more you test, the more **confidence** you gain in the system's reliability.
### Key Testing Concepts
- **Verification**: Are we building the product right?
- **Validation**: Are we building the right product?

![[Pasted image 20241023112806.png]]
## 6.2 Testing Techniques
### White Box Testing
- Also known as **Structural Testing**.
- **Key Techniques**:
  - **Basis Path Testing**: Analyzing the flow of control in the code.
  - **Condition Testing**: Ensuring that all **true/false** conditions are covered.
  - **Loop Testing**: Testing various iterations through loops.

![[Pasted image 20241115111353.png|400]]

### Black Box Testing
- Also known as **Functional Testing**.
- Test cases are based on the external **specifications**.
- **Equivalence Partitioning** and **Boundary Value Analysis** are common techniques.

![[Pasted image 20241115111417.png|400]]

### Fuzz Testing
- Injects random data (fuzz) into the system to discover vulnerabilities.

## 6.3 Testing Strategies
### Unit Testing
- Ensures individual **components** function correctly.
- Conducted by developers before handing off components to the team.
### Integration Testing
- Tests the interaction between different **modules**.
- Helps identify defects in interfaces between components.
### Regression Testing
- Verifies that **existing functionality** remains unaffected after changes.
- Best done with **automation** to minimize manual effort.
### Acceptance Testing
- Performed by **end users** or their representatives to validate that requirements are met.
- **Alpha Testing**: Done in a controlled environment by the developer's team.
- **Beta Testing**: Conducted in a real-world environment by selected customers.
### More Testing Strategies
- **Recovery Testing**: Ensures the system can recover from failure.
- **Stress Testing**: Tests the system under extreme conditions.
- **Performance Testing**: Measures system **run-time performance** (e.g., speed, memory usage).

## 6.4 Agile Testing and DevOps
### The V-Model in Agile
- The **V-Model** is flipped to accommodate continuous testing.
- **Automation** is key for faster feedback loops.

![[Pasted image 20241125092100.png]]

### Agile Testing Quadrants
- Tests are divided into **four quadrants** based on their focus (technology vs. business) and how they are conducted (manual vs. automated).

![[Pasted image 20241125092202.png]]

### Test Automation
- Test automation is essential in an agile environment to ensure rapid feedback and **continuous integration**.

## 6.5 Advanced Coverage Techniques
### Code Coverage
- Code coverage tools measure the extent to which the code is exercised by tests.
- Types include:
  - **Line Coverage**
  - **Branch Coverage**
  - **Function Coverage**
### Modified Condition/Decision Coverage (MC/DC)
- **MC/DC** requires that each condition in a decision independently affects the outcome.
- Commonly required in safety-critical software (e.g., **DO-178C** for aviation).
### Mutation Testing
- Introduces deliberate changes (**mutants**) into the code to see if the tests can detect them.
- **A good test suite** should be able to "kill" the mutant by detecting the defect.

## 6.6 Key Testing Terminology
- **Defect (Fault)**: A mistake in design or code that may cause abnormal behavior.
- **Failure**: A deviation from the system's expected behavior during execution.
- **Error**: Input that causes a failure, which can be **transient** (temporary) or **permanent**.
- **Test Case**: A set of inputs and expected results designed to test a component.
- **Test Stub**: Dummy code simulating a component’s behavior to facilitate testing.
- **Test Driver**: Code used to run test cases and interact with stubs or the system under test.

## 6.7 Agile Testing
### Flipping the V
- Agile processes demand **continuous testing** throughout the development cycle.
### FIT Tables
- A tool for defining **acceptance tests** through user stories in a structured format.

---

## Key Points to Remember:

- **Testing**: A process to identify and reduce risks in the system.
- **White Box Testing**: Focuses on the internal structure and control flow.
- **Black Box Testing**: Based on external specifications without considering internal logic.
- **Unit Testing**: Verifies the correctness of individual components.
- **Integration Testing**: Ensures modules work correctly together.
- **Regression Testing**: Confirms changes don’t break existing functionality.
- **MC/DC**: Required for critical software systems, ensuring decision conditions are fully tested.
- **Mutation Testing**: Introduces errors to evaluate the **strength of the test suite**.
- **Equivalence Partitioning**: Divides input data into partitions to ensure all cases are covered.
- **Stress and Performance Testing**: Test the system's behavior under extreme or resource-constrained conditions.
- **Fuzz Testing**: Used to find security vulnerabilities by feeding random data.
- **Acceptance Testing**: Ensures the system meets the end user's requirements.
- **Test Automation**: Vital for regression and agile testing.