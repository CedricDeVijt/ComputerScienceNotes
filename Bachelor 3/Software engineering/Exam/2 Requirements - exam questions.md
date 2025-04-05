## You should know the answers to these questions

### Why should the requirements specification be understandable, precise and open?

A requirements specification must:

- **Be understandable** so stakeholders can agree on what is in and out of scope.
- **Be precise** so all parties can confirm agreement on inclusions/exclusions and test each requirement.
- **Be open** so developers have freedom to design optimal solutions by focusing on the "what" rather than the "how".

### What’s the relationship between a use case and a scenario?

- **Use Case:** A generic description of a transaction to achieve a goal, involving one or more actors.
- **Scenario:** An instance of a use case. It shows a typical example of execution. Scenarios include:
  - Primary (happy day path)
  - Secondary (alternate paths or error cases).

### Can you give 3 criteria to evaluate a system scope description? Why do you select these 3?

1.  **Clarity**: Ensures stakeholders understand system goals and boundaries.
2.  **Goal-Oriented**: Ensures focus on achieving specific, valuable objectives.
3.  **Inclusion of Quality Criteria**: Provides measurable benchmarks for success.

### Why should there be at least one actor who benefits from a use case?

At least one actor must benefit to justify the use case’s inclusion in the system. This ensures the use case has value and aligns with stakeholder needs.

### Can you supply 3 questions that may help you identifying actors? And use cases?

**Identifying Actors:**

1.  Who uses the system?
2.  Who maintains the system?
3.  Who provides or receives information from the system?

**Identifying Use Cases:**

1.  What functions does each actor require from the system?
2.  What triggers events in the system?
3.  How does the system respond to external events?.

### What’s the difference between a primary scenario and a secondary scenario?

- **Primary Scenario:** Describes the main, successful path to achieving the goal.
- **Secondary Scenario:** Describes alternate paths, error handling, or exceptional conditions.

### What’s the direction of the \<\<extends\>\> and \<\<includes\>\> dependencies?

- **\<\<extends\>\>:** From the base use case to the extending use case, showing optional or conditional behavior.
- **\<\<includes\>\>:** From the including use case to the included use case, showing mandatory behavior.

### What is the purpose of technical stories in scrum?

Technical stories address non-functional requirements (e.g., performance, security). They help articulate technical improvements or constraints while educating product owners and assessing risks.

### List and explain briefly the INVEST criteria for user stories.

1.  **Independent:** Stories should not depend on others.
2.  **Negotiable:** Allows open discussion with stakeholders.
3.  **Valuable:** Provides clear benefits to the user.
4.  **Estimable:** Can be estimated for effort or size.
5.  **Small:** Achievable within a single sprint.
6.  **Testable:** Clear acceptance criteria.

### Explain briefly the three levels of detail for Product Backlog Items (Epic, Features, Stories).

1.  **Epic:** Large objectives taking months; spans multiple releases.
2.  **Features:** Medium-sized, spanning weeks; bigger than a sprint.
3.  **Stories:** Small, actionable items; completed within days.

### What is a minimum viable product?

An MVP is the smallest version of a product that provides value to users while allowing feedback for iterative development.

### Define a misuse case.

A misuse case describes a negative scenario or hostile intent against the system. It includes "threatens" and "mitigates" relationships to regular use cases.

### Define a safety story.

A safety story specifies measures to prevent hazards or reduce their impact. It uses structured templates like EARS (Event-Driven, State-Driven, etc.).

## You should be able to complete the following tasks

### Write a requirements specification for your bachelor capstone project.

...

## Can you answer the following questions?

### Why do use cases fit well in an iterative/incremental development process?

Use cases focus on delivering value incrementally by defining transactions that align with evolving requirements during iterations.

### Why do we distinguish between primary and secondary scenarios?

Distinguishing them ensures the system is tested for both ideal and exceptional paths, improving robustness.

### What would you think would be the main advantages and disadvantages of use cases?

**Advantages:**

- Clear communication of system behavior.
- Traceability to requirements.

**Disadvantages:**

- May become complex for large systems.
- Hard to maintain consistency across iterations.

### How would you combine use-cases to calculate the risky path in a project plan?

Analyze the dependencies and risk factors in each use case and combine them to form a "risky path" that identifies potential bottlenecks or critical challenges.

### Do use-cases work well with agile methods? Explain why or why not.

Yes, use cases work well in Agile because they focus on delivering customer value incrementally and are adaptable during sprints. However, they may require more effort to maintain alignment with evolving user stories.

### Can you explain the use of a product roadmap in scrum?

The roadmap communicates the incremental delivery of features over time, aligning releases with business goals and priorities.

### Choose the three most important items in your “Definition of Ready” checklist. Why are these most important to you?

1.  **Clear business value:** Ensures alignment with stakeholder goals.
2.  **Testable acceptance criteria:** Facilitates validation.
3.  **Dependencies identified:** Prevents blockers during development.

### Can you relate scrum user stories to some of the principles in the Agile Manifesto?

Scrum user stories reflect:

- **Customer collaboration** by prioritizing user needs.
- **Responding to change** with iterative feedback loops.
- **Delivering working software** incrementally.

### How would you turn an FMEA analysis into a misuse case diagram?

Use potential failure modes as misuse cases, map their effects to threatened use cases, and add mitigation paths for each identified hazard.

### Elaborate on the relationship between an FMEA analysis and the variants of safety stories.

FMEA identifies potential failures and their impacts, which inform the creation of safety stories by specifying measures to mitigate identified hazards.
