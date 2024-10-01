## Introduction
- **When, Why, Where, What**: Understand the context and details of requirement development.

## 2.1 Iterative Development with Use Cases
### Inception
- **Scope Definition & Risk Identification**: Determine project boundaries and potential challenges.
- **Actors & Use Cases**: Identify all entities interacting with the system.
- **Project Plan**: Establish development timelines and milestones.

### Elaboration
- **Primary & Secondary Scenarios**: Differentiate between the main ("happy day") and alternative scenarios.
  - **Primary Scenario**: Success scenarios assuming no issues.
  - **Secondary Scenario**: Alternative paths and error conditions.

## 2.2 Scrum & User Stories
### User Stories Components
- **Behavior Driven Template**: "As a `<user role>`, I want `<goal>` so that `<benefit>`."
- **Conditions of Satisfaction**: Criteria defining the expected outcome of a story.
- **INVEST Criteria**:
  - **I**ndependent: No dependencies.
  - **N**egotiable: Open to changes.
  - **V**aluable: Must provide customer value.
  - **E**stimable: Small enough to estimate.
  - **S**mall: Completable within one sprint.
  - **T**estable: Acceptance criteria defined.

### Scrum Details
- **Definition of Ready**: Checklist to ensure a story is ready for development.
  - **Checklist Examples**:
    - Business value clearly articulated.
    - Dependencies identified.
    - Acceptance criteria defined and testable.

- **Granularity Levels**:
  - **Epic**: Long-term goals.
  - **Features**: Completed in weeks.
  - **Sprintable Stories**: Ready for development in one sprint.

### Product Roadmap & MVP
- **Product Roadmap**: Communicates incremental product release plan.
- **Minimum Viable Product (MVP)**: Basic product version to gather user feedback.

## 2.3 Safety Critical Requirements
### Misuse Cases
- **Definition**: Use cases from the viewpoint of a hostile actor.
- **Purpose**: Identify and mitigate security threats.
  - **Threatens** & **Mitigates** Relationships: Show dependencies between use and misuse cases.

### Safety Stories
- **Purpose**: Prevent hazards or reduce impact.
  - **Templates**:
    - **Ubiquitous**: Component always responds.
    - **Event Driven**: Response triggered by an event.
    - **State Driven**: Response based on system state.

## 2.4 Requirements Management
### Scope Definition
- **Criteria**:
  - Short and goal-oriented description.
  - Includes criteria for success and failure.

### Identifying Risks
- **Risk Factors**:
  - Identify early issues (e.g., competition, market trends, supplier reliability).

### System Boundaries & Actors
- **System Boundaries**: Internal vs. external functions.
- **Identifying Actors**:
  - **Primary Actor**: Benefits from use case.
  - **Secondary Actor**: Supports the goal of the primary actor.

## 2.5 Conclusion
### Use Cases vs. User Stories
- **Understandable**: Clear roles for actors.
- **Precise**: Use scenarios to ensure detailed testing.
- **Open**: Focus on what to achieve, not how.

### Requirements Correctness & Traceability
- **Correctness**: Validation through black-box tests.
- **Traceability**: Requirements linked to design and project milestones.

