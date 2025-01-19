# Study Guide: Requirements Engineering

## 2.1 Introduction to Requirements

### When to Define Requirements?

- **Understandable**: Helps in deciding in-scope and out-of-scope elements.
- **Precise**: Allows agreement and testing.
- **Open**: Enables developers to choose optimal solutions by focusing on "what" not "how".

### Why Requirements Matter?

- Aligns numerous stakeholders despite limited resources.
- Ensures clarity in project goals and scope.

### Where Requirements Fit?

- **Functional Requirements**: Address end-user demands.
- **Non-Functional Requirements**: Focus on system constraints and quality attributes (e.g., performance, usability).

## 2.2 Use Cases

### What are Use Cases?

- **Definition**: Describe visible requirements of the system.
- **Components**:

  - Actor:

    - An **Actor** represents any entity that interacts with the system:
    - Can be **people, external systems**, or other components.
    - **Primary Actors** have unmet goals needing system assistance.
    - **Secondary Actors** provide help in achieving these goals.

  - Scenario
    - A **Scenario** is a specific instance of a **use case**:
    - **Primary Scenario**: Represents a typical successful outcome.
    - **Secondary Scenario**: Shows alternate paths or error handling, detailing how the system reacts to specific situations.

* **Scope**: Brainstorming to detailed specifications.
* **Audience**: End-users vs. developers.
* **Granularity**: From summaries to detailed steps.
* **Perspective**: Black-box (external view) vs. white-box (process view).

### System Scope and Boundaries

- **Define Scope**: Short, clear description with end-user commitment.
- **Identify Boundaries**:
  - Internal functionality (use cases).
  - External dependencies (actors).

### Identifying Actors and Use Cases

Key questions include:

- Who uses, installs, or maintains the system?
- What external systems or events interact with the system?

## 2.3 Agile and Scrum Approaches

### User Stories in Scrum

- **Template**:
  - As a , I want to , so that .
- **Conditions of Satisfaction**: Define criteria for acceptance.

### INVEST Criteria for User Stories

- **Independent**: Avoid dependencies.
- **Negotiable**: Encourage discussions with customers.
- **Valuable**: Deliver customer benefits.
- **Estimable**: Facilitate cost evaluation.
- **Small**: Fit into a single iteration.
- **Testable**: Provide clear acceptance criteria.

### Product Backlog Levels

- **Epics**: Broad features (months).
- **Features**: Mid-level tasks (weeks).
- **Stories**: Sprint-ready items (days).

### Minimum Viable Product (MVP)

- **Definition**: Early version with just enough features for feedback.
- **Purpose**: Gather insights for future development.

## 2.4 Safety-Critical Requirements

### Misuse Cases

- **Definition**: Negative scenarios focusing on hostile intent.
- **Elements**:
  - **Misuse Case**: Threatens ordinary use cases.
  - **Mitigates Relationship**: Indicates controls to counteract threats.

### Safety Stories

- **Template Variants**:
  - **Ubiquitous**: "The shall ."
  - **Event-Driven**: "When , the shall ."
  - **State-Driven**: "While , the shall ."

## 2.5 Planning and Risk Management

### Risk Identification

- Examples of risk factors:
  - Competitors and market trends.
  - Technical dependencies and team expertise.
  - Potential disasters (e.g., supply chain issues).

### Project Planning

- Use scope and risk factors to prioritize use cases.
- Follow two rules:
  - Developers estimate costs.
  - Customers assign priorities.

---

## Key Points to Remember

1. **Requirements Characteristics**:
   - Understandable, precise, and open.
2. **Use Case Components**:
   - Actors, scenarios, and system boundaries.
3. **Agile Principles**:
   - INVEST criteria and backlog hierarchy.
4. **MVP**:
   - Early feedback mechanism.
5. **Safety-Critical Practices**:
   - Misuse cases and safety stories for risk mitigation.
6. **Planning and Risk**:
   - Prioritize based on cost estimates and customer priorities.
