## You should know the answers to these questions

### What is (a) Testing, (b) a Testing Technique, (c) a Testing Strategy

- **(a) Testing**: The process of executing a program or system to find errors, verifying requirements are met, and ensuring the system behaves as expected.
- **(b) Testing Technique**: A method to design test cases to uncover defects, such as basis path testing or equivalence partitioning, focusing on specific aspects like code structure or input domains.
- **(c) Testing Strategy**: A plan dictating when and which testing techniques to apply to achieve confidence in system reliability, such as unit testing or regression testing, guiding the overall testing

### What is the difference between an error, a failure and a defect?

- **Error**: A human mistake, such as incorrect operation or usability issue, leading to incorrect system behavior.
- **Failure**: The system’s deviation from expected behavior, observable when a defect manifests during execution.
- **Defect**: A design or coding mistake (fault) that may cause abnormal behavior, including omissions or incorrect entries in design or code.

### What is a test case? A test stub? A test driver? A test fixture?

- **Test Case**: A set of inputs, execution conditions, and expected outputs designed to verify a specific aspect of the system.
- **Test Stub**: A simplified implementation of a component’s interface to simulate its behavior during testing.
- **Test Driver**: A program or script that executes test cases by providing inputs and checking outputs.
- **Test Fixture**: The setup or environment (e.g., data, objects) required to run a test case consistently (implied in gTest examples, Page 18).

### What are the differences and similarities between basis path testing, condition testing and loop testing?

- **Similarities**:
  - All are white-box testing techniques, relying on the internal structure of the code.
  - Aim to maximize code coverage and detect defects by exercising different code paths or conditions.
- **Differences**:
  - **Basis Path Testing**: Focuses on covering independent control flow paths, using cyclomatic complexity to determine the minimum number of paths.
  - **Condition Testing**: Tests all true/false combinations of conditions in complex boolean expressions, ensuring assertions and decision points are exercised.
  - **Loop Testing**: Targets loop constructs, testing iterations (0, 1, N times) to ensure proper loop behavior.
  - **Complementary Nature**: Basis path testing covers overall control flow, condition testing ensures detailed condition coverage, and loop testing focuses on iterative structures, together providing comprehensive code coverage.

### How many tests should you write to achieve MC/DC coverage? And multiple condition coverage?

- **MC/DC (Modified Condition/Decision Coverage)**:
  - Requires a number of tests equal to **n + 1**, where **n** is the number of independent conditions in a decision, ensuring each condition independently affects the outcome while others remain constant.
  - Example: For 3 conditions, typically 4 tests are needed.
- **Multiple Condition Coverage**:
  - Requires **2^n** tests, where **n** is the number of conditions, to cover all possible true/false combinations of conditions.
  - Example: For 3 conditions, 8 tests are needed (2^3).

### Where do you situate alpha/beta testing in the four quadrants model?

- The four quadrants model categorizes tests by purpose (e.g., technology-facing vs. business-facing, supporting team vs. critiquing product).
- **Alpha Testing**: Fits in **Quadrant 3** (business-facing, critiquing product), as it involves end-users testing in a controlled environment to verify requirements.
- **Beta Testing**: Fits in **Quadrant 3** (business-facing, critiquing product), as it involves selected customers testing in uncontrolled environments.

### What are the differences and similarities between unit testing and regression testing?

- **Similarities**:
  - Both aim to ensure system correctness and detect defects.
  - Often automated to improve efficiency and repeatability.
  - Can use similar testing techniques (e.g., white-box or black-box) depending on the context.
- **Differences**:
  - **Unit Testing**: Focuses on testing individual components in isolation to catch local defects, performed by developers during development.
  - **Regression Testing**: Ensures that new changes (e.g., fixes, updates) do not break existing functionality, involving a subset of tests run repeatedly after changes.
  - **Scope**: Unit testing is narrower (component-level), while regression testing spans multiple levels (unit, integration, system).

### How do you know when you tested enough?

- Testing is sufficient when:
  - The failure rate is below an acceptable risk threshold, determined through statistical testing.
  - All planned test cases are specified and executed, achieving adequate coverage (code, requirements, test coverage).
  - No new defects are found, or testing exhausts time/budget constraints.
  - Each bug fix is accompanied by a new test to prevent regression.

### What is Alpha-testing and Beta-Testing? When is it used?

- **Alpha Testing**: Conducted by end-users at the developer’s site in a controlled environment to verify requirements for off-the-shelf software before release. pre-release stage.
- **Beta Testing**: Conducted by selected customers in real-world settings without developers present, testing the software’s performance in actual usage conditions. diverse, uncontrolled environments before final release.

### What is the difference between stress-testing and performance testing?

- **Stress Testing**: Tests system behavior under extreme conditions (e.g., excessive input rates) to check if it fails gracefully or recovers properly, focusing on resilience.
- **Performance Testing**: Evaluates system runtime performance (e.g., time, memory consumption) under normal or specified conditions to ensure efficiency and scalability.

- **Difference**: Stress testing pushes the system beyond normal limits to test failure and recovery, while performance testing measures efficiency within expected usage scenarios.

---

## You should be able to complete the following tasks

### Complete test cases for the Loop Testing example (Loop Testing on page 19).

- Identify the loop types (simple, nested, concatenated).
- Define test cases for:
  - Zero iterations (bypassing the loop).
  - One iteration.
  - Maximum iterations.
  - Iterations just beyond the maximum (if applicable).
- Include edge cases for loop conditions and any data dependencies.

### Rewrite the binary search so that basis path testing and loop testing becomes easier.

- Refactor the binary search function to:
  - Explicitly separate conditional and loop constructs.
  - Use clear, distinct paths for edge cases (e.g., element not found, first/middle/last element found).
- Simplify nested conditions and ensure each path corresponds to a unique basis path.

### Write a piece of code implementing a quicksort. Apply all testing techniques (basis path testing, conditional testing [3 variants], loop testing, equivalence partitioning) to derive appropriate test cases.

- Implement quicksort using recursion and partitioning.
- Derive test cases for:
  - **Basis Path Testing:** Cover recursive calls, base cases, and partition scenarios.
  - **Condition Testing (3 Variants):**
    - Simple condition testing for pivot selection.
    - Branch condition testing for comparisons in the partition step.
    - Compound condition testing for complex conditions in loops and recursion.
  - **Loop Testing:** Validate the partition loop for zero, one, and many iterations.
  - **Equivalence Partitioning:** Partition input arrays into:
    - Sorted arrays.
    - Reverse-sorted arrays.
    - Arrays with duplicate elements.

### Write FIT test cases for the user stories in your Bachelor Capstone Project.

- Identify user stories and their acceptance criteria.
- Create FIT (Framework for Integrated Testing) tables for:
  - Inputs: Parameters or actions users perform.
  - Expected Outputs: Results or behaviors the system should produce.
- Example FIT Table for a login feature:
  | **Input** | **Expected Output** |
  |---------------------|---------------------------|
  | Valid credentials | Login successful |
  | Invalid credentials | Error message displayed |

### Apply fuzz testing to the REST-API of your project.

- Use fuzz testing tools (e.g., OWASP ZAP, Postman Fuzz Testing, or custom scripts) to:
  - Generate random or malformed inputs for API endpoints.
  - Test for unexpected behavior (e.g., crashes, errors, or security vulnerabilities).
- Define metrics for evaluating the results, such as error logs or response times.

## Can you answer the following questions?

### You’re responsible for setting up a test program. To whom will you assign the responsibility to write tests? Why?

- Assign responsibilities to:
  - Developers: Write unit tests since they understand the code logic.
  - Testers/QA Engineers: Write integration and system tests to ensure objectivity.
  - Product Owners or Stakeholders: Provide input for acceptance tests to align with user expectations.

### Why do we distinguish between several levels of testing in the V-model?

- To ensure thorough validation at each development stage.
- To match testing activities with corresponding phases (e.g., unit testing with implementation, system testing with integration).
- To reduce defects early and minimize costs of fixing them later.

### Explain why basis path testing, condition testing, and loop testing complement each other.

- **Basis Path Testing:** Ensures all independent paths are tested.
- **Condition Testing:** Validates logical decisions and their outcomes.
- **Loop Testing:** Focuses on loop-specific scenarios.
- Combined, they address different code structures, ensuring comprehensive coverage.

### Why is mutation coverage a better criterion for assessing the strength of a test suite?

- It measures the test suite's ability to detect small changes (mutations) in the code, simulating potential defects.
- A higher mutation coverage indicates a robust suite capable of catching subtle bugs.

### Explain fuzzing (fuzz testing) in your own words.

- Fuzzing is a testing technique where random, invalid, or unexpected inputs are provided to a system to identify vulnerabilities, crashes, or unexpected behavior.

### Explain what FIT tables are.

- FIT (Framework for Integrated Testing) tables are structured representations of test cases, showing inputs, actions, and expected outputs. They bridge communication between stakeholders and developers by aligning tests with requirements.

### When would you combine top-down testing with bottom-up testing? Why?

- Combine these approaches in a **hybrid testing strategy** when:
  - Both higher-level modules (top-down) and lower-level utilities (bottom-up) are critical.
  - Immediate feedback on integration is needed while testing lower-level components.

### When would you combine black-box testing with white-box testing? Why?

- Use both when:
  - You need to validate external functionality (black-box) and internal code structure (white-box).
  - The system must meet user expectations and maintain code quality.

### Is it worthwhile to apply white-box testing in an OO context?

- Yes, as it verifies object interactions, method behaviors, and code-level details, ensuring robust encapsulation and inheritance implementations.

### What makes regression testing important?

- Ensures that new changes or fixes do not introduce unintended defects.
- Maintains system stability over time.

### Is it acceptable to deliver a system that is not 100% reliable? Why (not)?

- It depends on the context:
  - **Critical Systems (e.g., medical, aviation):** No, as reliability is essential for safety.
  - **Non-critical Systems:** Yes, if defects do not significantly impact users and deadlines must be met.

### Explain the subtle difference between code coverage and test coverage.

- **Code Coverage:** Measures the percentage of code executed by tests.
- **Test Coverage:** Evaluates the extent to which requirements or functionality are tested, which may not directly correlate with code execution.
