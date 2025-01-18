## 2.1 Introduction

### When, Why, Where, What are Requirements?

- **When**: Requirements should be established at the inception of a project to clearly define goals and scope.
- **Why**: Helps balance **numerous stakeholders** and **limited resources**.
- **Where**: Requirements are divided into:
  - **Functional Requirements**: The functions demanded by end users.
  - **Non-functional Requirements**: Constraints like **performance**, **maintainability** and **usability**.

## 2.2 Use Cases and User Stories

### Use Case

- A **Use Case** a use case describes how a user interacts with the system to achieve a specific goal.
- It is a **generic description** of a complete transaction to achieve a specific goal involving one or more **actors**.

### Actor

- An **Actor** represents any entity that interacts with the system:
  - Can be **people, external systems**, or other components.
  - **Primary Actors** have unmet goals needing system assistance.
  - **Secondary Actors** provide help in achieving these goals.

### Scenario

- A **Scenario** is a specific instance of a **use case**:
  - **Primary Scenario**: Represents a typical successful outcome.
  - **Secondary Scenario**: Shows alternate paths or error handling, detailing how the system reacts to specific situations.

### Iteratively Developing Use Cases

- **Inception Phase**: Define system scope, including:
  - **Scope Definition**: Clear statement outlining what lies inside and outside the system.
  - **Risk Identification**: Early identification of risks such as competitors, market trends, and technical dependencies.
- **Elaboration Phase**:
  - **Scenarios**: Use cases are broken into **primary (success)** and **secondary (alternative)** scenarios.

#### Kinds of Use Cases

- **Scope**: Can range from brainstorming ideas to a fully-detailed specification.
- **Granularity**:
  - **Brief Use Case**: High-level overview.
  - **Fully Dressed Use Case**: Detailed, with all steps included.
- **Black-box vs. White-box**: Depending on knowledge about the processes involved.

### Unified Process

- **Inception & Elaboration Phases**:
  - Use cases work well in iterative development, often evolving from inception (scope definition) to elaboration (scenario refinement).

## 2.3 Scrum Requirements

### User Stories

- Stories describe features from the perspective of different user roles:
  - Template:
    - "As a `<user role>`, I want to `<goal>`, so that `<benefit>`."
- **Conditions of Satisfaction**: Details used to verify the story's completeness.

#### INVEST Criteria for User Stories

- **I - Independent**: Each story should be independent of others.
- **N - Negotiable**: Avoid too much detail that limits discussion.
- **V - Valuable**: Must deliver value to the customer.
- **E - Estimable**: Size of the story should be estimable.
- **S - Small**: Should fit within a single iteration.
- **T - Testable**: Clearly defined acceptance criteria.

### Definition of Ready

- Checklist to determine if a Product Backlog Item is ready to be moved to a sprint:
  - **Business value is articulated**.
  - **Dependencies are identified**.
  - **Acceptance criteria are clear and testable**.

### Product Backlog and Roadmap

- **Levels of Detail**:
  - **Epic**: Takes months and spans beyond a release.
  - **Feature**: Takes weeks and spans multiple sprints.
  - **Sprintable Stories**: Smaller chunks to be completed within a sprint.

## 2.4 Safety Critical Requirements

### Misuse Cases

- Describes potential hostile actions against the system.
- **Negative Scenarios**: Also known as **Failure Mode and Effects Analysis (FMEA)**.
- **Mitigates/Threatens Relationships**: Specify how certain features mitigate or are threatened by hostile use cases.

#### Example of Misuse Case

- **Car Theft Scenario**:
  - **Driver locks car** (mitigates)
  - **Thief shortcuts ignition** (threatens)

### Safety Stories

- Stories aimed at preventing hazards or reducing impact.
- **Extended Template (EARS)**:
  - **Ubiquitous**: "The component shall respond."
  - **Event Driven**: "When [trigger], the system shall respond."
  - **State Driven**: "While in a specific state, the system shall respond."

## Conclusion and Correctness

- **Correctness and Traceability**:
  - **Validation**: Ensuring the solution matches requirements via tests.
  - **Traceability**: Linking requirements to system elements, ensuring milestones are met.

---

## Key Points to Remember

- **Requirements are critical** to set expectations and define project scope.
- **Use Cases**:
  - Describe **transactions** between actors to achieve a goal.
  - **Scenarios** provide specific examples of use case execution.
- **Scrum User Stories**:
  - Should follow the **INVEST criteria** for efficient development.
  - Are validated by **Conditions of Satisfaction**.
- **Definition of Ready** ensures backlog items are prepared for development.
- **Misuse Cases**:
  - Represent potential threats.
  - Useful for safety and security analysis.
- **Safety Stories**:
  - Aim to mitigate hazards, ensuring system safety.
