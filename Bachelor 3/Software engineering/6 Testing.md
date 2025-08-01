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


# Software Testing: Principles, Techniques, and Strategies

This chapter provides a comprehensive overview of software testing, emphasizing its role as a risk reduction activity to ensure system reliability. It covers the timing, purpose, and execution of testing, along with key terminology, techniques, and strategies. The content is structured to clarify the distinction between verification and validation, explore white-box and black-box testing methods, and address practical considerations like when to stop testing. By linking testing to risk management and quality assurance, this chapter equips learners with a holistic understanding of testing in software development.

## When to Test: Aligning Testing with Development Processes

Testing should commence as early as possible to mitigate risks and ensure alignment with project schedules. The **Unified Process** and **V-Model** provide frameworks for integrating testing throughout the development lifecycle. Early testing reduces the cost of fixing defects and builds confidence in the system’s reliability.

### Unified Process: Testing as Risk Reduction

The Unified Process views testing as a continuous activity to reduce risks. It emphasizes starting testing during the **requirements phase** to assess and mitigate schedule risks.

- **Key Idea**: Testing spans from requirements to deployment, ensuring defects are caught early.
- **Example**: Testing prototypes during analysis reduces misunderstandings in requirements.

### V-Model: Designing with Testability in Mind

The V-Model aligns testing with development phases, advocating for test preparation during **module specification** and design. It ensures that each development stage has a corresponding testing phase.

- **Process**: Specify and design components with testability, preparing test cases concurrently.
- **Benefit**: Early test design catches specification flaws, reducing downstream errors.

![[Pasted image 20241023110234.png]]

## Why Test: Risk Management and Confidence Building

Testing is a **risk management** activity that demonstrates the presence of defects but cannot prove their absence (E.W. Dijkstra). It increases confidence in the system by reducing the likelihood of harmful defects.

### Testing as a Risk Report

Testing produces a **risk report** for project management, informing **go/no-go decisions** for product release.

- **Counterargument to Skipping Testing**: While defects may persist, thorough testing minimizes their impact.
- **Outcome**: A well-tested system supports confident deployment decisions.

### Practical Implications

The more rigorous the testing, the greater the assurance that the system will perform as expected.

- **Example**: A banking application tested extensively for transaction errors inspires trust.
- **Link to Later Sections**: This confidence ties to coverage metrics like MC/DC in safety-critical systems.

## What is Testing: Verification vs. Validation

Testing verifies that a system meets its **specifications** (building the product right) but does not validate whether it meets user needs (building the right product). It involves executing a program to identify **defects**.

### Definition and Scope

Software testing, per Myers (1979), is the process of executing a system to find **errors**. A successful test uncovers defects, aligning with the goal of risk reduction.

- **Verification**: Ensures the system adheres to its design and requirements.
- **Validation**: Ensures the system fulfills its intended purpose (not the focus of testing).

### Testing Techniques and Strategies

**Testing techniques** maximize the probability of finding defects, measured by **coverage** (code, requirements, risks). **Testing strategies** dictate when and how to apply techniques to build deployment confidence.

- **Technique Example**: Basis path testing ensures all code paths are executed.
- **Strategy Example**: Regression testing ensures changes don’t introduce new defects.

## Who Should Test: Roles and Responsibilities

Testing is a **destructive activity** (trying to make systems fail), contrasting with the **constructive nature** of programming. Different roles ensure objectivity and thoroughness.

### Developers vs. Specialized Testers

Programmers perform **unit tests** to verify components, while specialized test teams handle **integration**, **system**, and **acceptance tests** for broader scope.

- **Why Separate Roles?**: Developers may overlook defects due to bias toward their code.
- **Example**: A test team uncovers integration issues missed during unit testing.

### Quality Assurance Context

Testing is part of **quality assurance**, ensuring defects are identified and addressed before release.

- **Unit Testing**: Done by developers to verify individual components.
- **System Testing**: Conducted by testers to validate subsystem interactions.

## What is Correct: Defining System Behavior

A system is **correct** if it behaves according to its **specification**, though correctness is theoretically undecidable. Practical measures focus on reliability and robustness.

### Correctness and Reliability

Correctness is an absolute property (a system is either correct or not), while **reliability** is relative (e.g., mean time between failures).

- **Robustness**: A system behaves reasonably under unspecified conditions.
- **Example**: A web server handling unexpected traffic spikes demonstrates robustness.

### Practical Considerations

Users rely on systems to operate as expected, with testing reducing the probability of failures.

- **Link to Coverage**: Metrics like code coverage quantify how much of the specification is tested.
- **Source Reference**: [Ghez02] highlights representative qualities of correctness.

## Terminology: Precision in Testing Language

Precise terminology distinguishes between **defect**, **failure**, and **error**, avoiding ambiguous terms like “bug.” The IEEE Glossary and ISTQB standards provide clarity.

### Key Definitions

- **Defect/Fault**: A design or coding mistake causing abnormal behavior.
  - **By Omission**: Missing functionality or logic.
  - **By Commission**: Incorrect implementation.
- **Failure**: A deviation from the specification during execution.
- **Error**: The input triggering a failure (transient or permanent).

### Bug Tracking Workflow

The workflow categorizes issues as **errors**, **defects**, **usability issues**, or **feature requests**, ensuring accurate resolution.

- **Example**: An “operator error” may indicate a usability issue, not a defect.
- **Common Pitfall**: Using “bug” imprecisely can confuse defect tracking.

### Testing Components

- **Component**: A testable part of the system (e.g., an object or subsystem).
- **Test Case**: Inputs and expected results to verify component behavior.
- **Test Stub**: Dummy code simulating dependencies.
- **Test Driver**: Code executing test cases.
- **Test Fixture**: A fixed state for consistent testing.

## White-Box Testing: Internal Structure Focus

**White-box testing** leverages knowledge of a system’s internal structure to design test cases. It includes techniques like **basis path testing**, **condition testing**, and **loop testing**.

### Basis Path Testing

Basis path testing uses a **control flow graph** to identify independent execution paths, measured by **cyclomatic complexity** (\( V(G) = E - N + 2 \), where \( E \) is edges and \( N \) is nodes).

- **Steps**:
  1. Draw the control flow graph.
  2. Compute cyclomatic complexity to determine the number of paths.
  3. Design test cases to cover all paths.
- **Example**: A binary search function with a cyclomatic complexity of 5 requires up to 5 test paths.

### Condition Testing

Condition testing ensures all **true/false combinations** of conditions are tested, including **multiple condition coverage** and **domain testing**.

- **Types**:
  - **Condition Coverage**: Each condition’s true/false outcomes.
  - **Multiple Condition Coverage**: All combinations of conditions.
  - **Domain Testing**: Tests boundary conditions (e.g., \( a < b \), \( a \leq b \)).
- **Example**: For \( (x > y) \&\& (x > z) \), test all combinations of \( x \), \( y \), and \( z \).

### Loop Testing

Loop testing verifies loops by executing them **zero**, **once**, and **multiple times**.

- **Purpose**: Ensures loops handle boundary cases correctly.
- **Example**: Testing a loop with inputs that trigger no iterations, one iteration, and several iterations.

### White-Box in Object-Oriented Contexts

White-box testing is less effective in **object-oriented systems** due to complex object compositions and polymorphism. **Sequence** and **collaboration diagrams** are better suited for testing interactions.

- **Challenge**: Internal structure is obscured by encapsulation.
- **Solution**: Focus on behavioral testing using black-box techniques.

## Coverage Metrics: Measuring Test Effectiveness

**Coverage** quantifies how thoroughly a test suite exercises a system, including **code coverage**, **MC/DC coverage**, and **mutation coverage**.

### Code Coverage

Code coverage measures the percentage of code executed by tests, typically lines or statements.

- **Tool Support**: Tools like gTest instrument code to track execution.
- **Example**: The `findLast` function tests ensure all lines are executed.

### Modified Condition/Decision Coverage (MC/DC)

MC/DC, required for safety-critical systems (e.g., DO-178C, ISO 26262), ensures each condition independently affects a decision’s outcome.

- **Requirements**:
  - Each entry/exit point is invoked.
  - Each decision and condition takes all outcomes.
  - Each condition independently influences the decision.
- **Example**: For \( A \&\& B \), test cases show \( A \) and \( B \) independently affecting the result.

### Mutation Coverage

Mutation testing injects faults (mutants) into code to assess test suite strength. A test “kills” a mutant if it detects the fault.

- **Process**: Modify code (e.g., change \( i \geq 0 \) to \( i > 0 \)) and run tests.
- **Example**: Adding a boundary test for `findLast` kills a mutant altering the loop condition.

## Black-Box Testing: Specification-Based Testing

**Black-box testing** treats the system as a “black box,” deriving test cases from its **external specification** without knowledge of internal structure.

### Equivalence Partitioning and Boundary Value Analysis

**Equivalence partitioning** divides inputs into classes where the system behaves similarly. **Boundary value analysis** tests edges of these classes.

- **Steps**:
  1. Identify input domains (e.g., ranges, values, sets).
  2. Divide into valid and invalid equivalence classes.
  3. Select test data, prioritizing boundaries.
  4. Predict outputs for test cases.
- **Example**: For an input range \( 1 \leq x \leq 100 \), test \( x = 1 \), \( x = 100 \), \( x = 0 \), and \( x = 101 \).

### Fuzz Testing

**Fuzz testing** inputs massive random data to uncover **security vulnerabilities** or unexpected behaviors.

- **Application**: Commonly used for REST APIs or user interfaces.
- **Example**: Sending malformed JSON to a REST endpoint to test error handling.

## Testing Levels: From Units to Systems

Testing occurs at multiple levels, each addressing different system aspects: **unit**, **integration**, **regression**, and **acceptance testing**.

### Unit Testing

Unit testing verifies individual components, typically by developers using frameworks like gTest.

- **Limitation**: Passing unit tests doesn’t guarantee system correctness.
- **Example**: The `findLast` tests verify specific function behaviors.

### Integration Testing

Integration testing checks interactions between modules, identifying interface defects.

- **Approach**: Combine modules and test their collective behavior.
- **Example**: Testing a database and API module interaction.

### Regression Testing

Regression testing ensures changes don’t introduce new defects, re-executing tests after modifications.

- **Automation**: Essential for frequent execution (e.g., nightly builds).
- **Challenge**: High initial investment in test maintenance.

### Acceptance Testing

Acceptance testing, conducted by end-users, verifies requirements implementation. It includes **alpha testing** (controlled environment) and **beta testing** (real-world setting).

- **Purpose**: Balances verification and validation.
- **Example**: Beta testing a mobile app with select customers.

## Additional Testing Strategies

Beyond core testing levels, specialized strategies address specific system attributes.

### Recovery and Resilience Testing

Tests system recovery from failures, critical for **fault-tolerant systems**.

- **Example**: Simulating a server crash to verify data recovery.

### Stress and Performance Testing

**Stress testing** evaluates system behavior under extreme conditions, while **performance testing** measures runtime efficiency (e.g., time, memory).

- **Example**: Stress testing a website with double the expected traffic.

### Back-to-Back Testing

Compares outputs of two system versions to ensure consistency.

- **Use Case**: Validating a new implementation against a legacy system.

## When to Stop Testing: Balancing Risk and Resources

Deciding when to stop testing involves balancing risk, time, and budget constraints. **Statistical testing** measures failure rates against acceptable thresholds.

### Practical Guidelines

- **Cynical Reality**: Testing stops when time or money runs out.
- **Strategic Approach**: Stop when risks are below acceptable levels.
- **Example**: A medical device may require near-zero failure rates, demanding extensive testing.

### Long-Term Benefits

Tests save time by catching defects early, despite initial investment.

- **Link to Regression Testing**: Automated tests reduce long-term maintenance costs.
- **Pitfall**: Pressure to skip testing can lead to costly failures.

## Tool Support: Enhancing Testing Efficiency

Tools like **test harnesses**, **code coverage tools**, **mutation testing tools**, and **capture-playback tools** streamline testing processes.

### Test Harness

A test harness automates deterministic tests, using **stubs** for input/output.

- **Benefit**: Predictable, repeatable test execution.
- **Example**: A harness for `findLast` automates boundary tests.

### Coverage and Mutation Tools

Coverage tools track executed code, while mutation tools assess test suite robustness.

- **Example**: gTest reports line coverage for unit tests.
- **Link to MC/DC**: Tools ensure compliance with safety standards.

### Capture-Playback Tools

Record and replay UI actions to verify consistent behavior.

- **Use Case**: Testing web application workflows.

## Agile Testing and DevOps

**Agile testing** integrates testing into iterative development, often using **FIT tables** for acceptance tests. **DevOps** emphasizes continuous testing in deployment pipelines.

- **FIT Tables**: Specify test scenarios linking user stories to outcomes.
- **Example**: A FIT table for a login feature tests valid/invalid credentials.

## Test Coverage: Beyond Code

**Test coverage** includes **code coverage** (lines, statements, MC/DC), **requirement coverage** (e.g., FIT tables), and **test plan coverage** (executed test cases).

- **Distinction**: Code coverage measures code execution, while test coverage tracks test case completion.
- **Example**: A test plan with 90% executed test cases may have 80% code coverage.

## Conclusion: Correctness, Traceability, and Quality

Testing ensures **correctness** (adherence to specifications), **traceability** (linking tests to requirements), and **quality** (reducing risks). It requires a strategic blend of techniques and tools tailored to project needs.

- **Traceability**: Ensures all requirements are tested.
- **Quality**: Balances reliability and robustness for user trust.

## Key Points to Remember

- **Testing → Risk Management**: Testing reduces risks but cannot prove defect absence. ★★★★★
- **Verification vs. Validation**: Testing verifies specifications, not user needs. ★★★★☆
- **White-Box → Basis Path Testing**: Uses cyclomatic complexity to cover code paths. ★★★★☆
- **Black-Box → Equivalence Partitioning**: Tests based on specifications, focusing on boundaries. ★★★★☆
- **Coverage → MC/DC**: Ensures conditions independently affect decisions in safety-critical systems. ★★★★☆
- **Regression Testing → Automation**: Prevents new defects after changes, requiring frequent execution. ★★★★☆
- **When to Stop → Statistical Testing**: Balances risk thresholds with resource constraints. ★★★★☆
- **Tools → Test Harness**: Automates repeatable tests for efficiency. ★★★★☆
