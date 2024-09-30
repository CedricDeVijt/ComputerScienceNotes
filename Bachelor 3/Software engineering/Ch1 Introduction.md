## 1.1 Software Engineering
### Why & What:
- **Product vs. Process:**
  - **Product:** What is delivered to the customer.
  - **Process:** Activities leading to the product, involving iterative and incremental development to manage risks.

### Correctness & Traceability:
- **Correctness:** Building the product right (Verification) and building the right product (Validation).
- **Traceability:** Ability to track relationships between requirements and product components.

## 1.2 Software Process
### Key Activities:
- **Requirements Collection**
- **Analysis** (defining "what")
- **Design** (defining "how")
- **Implementation**, **Testing**, **Maintenance**, and **Quality Assurance**

### Development Models:
- **Waterfall Model:**
  - Step-by-step process.
  - **Limitations:** Unrealistic for large projects, hard to manage changes, and late delivery of working versions.
![[Pasted image 20240930104129.png]]
- **Iterative and Incremental Development:**
  - **Iterative:** Reworking to improve.
  - **Incremental:** Small, tangible steps to produce early results.

### Sample Processes:
- **Unified Process, Spiral Model, Agile Development (XP, Scrum)**

## 1.3 Software Product
### Unified Modeling Language (UML):
- **Usage:** Standardized notation for modeling software systems, useful for managing complexity and supporting lifecycle processes.

# 1.4 Why Software Engineering?
- Questions to consider:
  - Where do the requirements come from?
  - How do we validate and verify the specifications?
  - How do we adapt to changes?
  - **Teamwork:** Managing communication and scale challenges in multi-person projects.

### Definitions and Issues:
- **"State of the art"**: Constantly evolving, demands **life-long learning**.
- **Teamwork** and **Multi-Version Development**: Software must evolve continuously.

## 1.5 Product and Process
### Key Differences:
- **Product:** System delivered to the customer.
- **Process:** Activities to create the product.

### Evaluation Criteria:
- **Validation (Correctness):** Are we building the right product?
- **Verification:** Are we building the product correctly?

## 1.6 Risk Analysis and Management
### Risk Types:
- **Project Risks:** E.g., staffing risks.
- **Technical Risks:** E.g., new technology.
- **Business Risks:** E.g., market demand uncertainty.

### Risk Assessment Process:
- **Risk Identification, Projection (Estimation), Assessment**
- **Impact and Likelihood:** Measured on scales to prioritize risks.

### Example: Failure Mode and Effects Analysis (FMEA)
- Identify potential failure modes, their effects, causes, and criticality to manage risk effectively.

# 1.7 Prototyping
- **Purpose:** To test, explore, or validate a hypothesis to reduce risks.
- **Types:**
  - **Exploratory Prototype (Throwaway):** To validate requirements or explore design choices.
  - **Evolutionary Prototype:** Evolving into the final product through iterations.
  
## 1.8 Agile Development
### Agile Manifesto Values:
- **Individuals & Interactions > Processes & Tools**
- **Working Software > Comprehensive Documentation**
- **Customer Collaboration > Contract Negotiation**
- **Responding to Change > Following a Plan**

### eXtreme Programming (XP):
- **Key Principles:**
  - **Fine Scale Feedback:** Pair programming, test-driven development.
  - **Continuous Process:** Continuous integration, refactoring.
  - **Shared Understanding:** Collective code ownership, simple design.
  - **Programmer Welfare:** Sustainable pace.
  
## 1.9 Scrum Process
### Key Concepts:
- **Sprint:** 2-4 week period to create a working product increment.
- **Daily Stand-up Meetings**
  
### Roles in Scrum:
- **Product Owner:** Prioritizes the backlog.
- **Scrum Master:** Facilitator.
- **Development Team:** 5-9 members responsible for increment delivery, **self-organizing**.

### Planning and Monitoring:
- **Task Points, Sprint Backlog, and Poker Planning**

# 1.10 Unified Modeling Language (UML)
### History and Evolution:
- **First Generation:** Booch, OMT.
- **Second Generation:** Fusion of proven ideas.
- **Third Generation:** Unified Modeling Language for a consistent and adaptable notation system.

### Static UML:
- **Classes and Associations:**
  - Represent relationships, aggregation, and composition.
  - **Generalization** represents inheritance.

### Dynamic UML:
- **Sequence Diagrams:** Show object interactions over time.
- **Collaboration Diagrams:** Represent relationships with messages between objects.


## You should know the answers to these questions:

### 1. How does Software Engineering differ from programming?
**Software Engineering** is a systematic, disciplined, and quantifiable approach to the development, operation, and maintenance of software. It includes requirements analysis, system design, testing, deployment, and maintenance. **Programming**, on the other hand, is just one aspect of software engineering, which involves writing code to implement specific functions or solutions. In short, software engineering encompasses the entire software development lifecycle, while programming is only a part of it.

### 2. Why is programming only a small part of the cost of a “real” software project?
Programming is only one phase in the entire process of software development. The majority of costs come from other phases such as requirements gathering, system design, documentation, testing, debugging, project management, user training, deployment, and ongoing maintenance. These activities often require a significant amount of time and resources compared to the actual act of writing code.

### 3. Give a definition for “traceability”.
**Traceability** refers to the ability to track and link software development artifacts through the entire lifecycle. This includes being able to trace requirements to their corresponding design elements, source code, and test cases, ensuring all features are implemented and verified.

### 4. What is the difference between analysis and design?
**Analysis** focuses on understanding and defining the problem that needs to be solved, including gathering requirements and modeling functional aspects. It is a "what" activity—identifying what needs to be done. **Design**, on the other hand, is about how to solve the problem—creating a system structure or architecture that will meet the requirements. It involves planning the solution.

### 5. Explain verification and validation in simple terms.
**Verification** is about checking whether the product is being built correctly (e.g., are we following the proper specifications and standards?). **Validation** is about checking whether we have built the right product (i.e., does the software meet the customer's needs and expectations?).

### 6. Why is the “waterfall” model unrealistic? Why is it still used?
The **waterfall model** is unrealistic because it assumes that each phase of the software development lifecycle must be completed fully before moving on to the next, with no iterations. In practice, requirements often change, and a linear approach makes it difficult to adapt to those changes. However, it is still used because it is simple, easy to manage, and suitable for smaller projects with well-defined requirements.

### 7. Can you explain the difference between iterative development and incremental development?
- **Iterative Development**: A process where the software is developed in repeated cycles (iterations), and each iteration improves the software by adding features or refining the product.
- **Incremental Development**: A process where the software is built in small, functional increments that are integrated over time. Each increment adds specific functionality to the system.
In practice, both are often used together, with increments being developed iteratively.

### 8. How do you decide to stop in the spiral model?
In the **spiral model**, the decision to stop is based on whether the goals for that cycle have been achieved and whether the risks identified have been sufficiently mitigated. Typically, the project stops once the product meets all required objectives, and no further risks or requirements justify additional iterations.

### 9. How do you identify risk? How do you assess a risk? Which risks require action?
**Identifying risk** involves looking for factors that could negatively impact the project, such as technical challenges, schedule delays, or scope creep. To **assess a risk**, you evaluate the likelihood of its occurrence and the potential impact if it happens. Risks with a high likelihood and high impact usually require action to either mitigate them or develop contingency plans.

### 10. What is Failure Mode and Effects Analysis (FMEA)?
**Failure Mode and Effects Analysis (FMEA)** is a systematic approach for identifying potential failure modes in a system, assessing their impact, and prioritizing them based on their severity, likelihood, and detectability. It helps to improve the reliability of the system by addressing potential issues early in the design or development phase.

### 11. List the 6 principles of extreme programming.
1. **Communication**: Ensure clear and continuous communication between the development team and stakeholders.
2. **Simplicity**: Focus on designing and coding only what is necessary.
3. **Feedback**: Obtain constant feedback from the client and through testing.
4. **Courage**: Be willing to make changes when needed, refactor code, or discard unnecessary features.
5. **Respect**: Foster a team culture where everyone’s contributions are valued.
6. **Continuous Improvement**: Refactor and iterate to constantly improve the code and processes.

### 12. What is a “sprint” in the SCRUM process?
A **sprint** in the SCRUM process is a time-boxed period (usually 1-4 weeks) in which a specific set of work must be completed and made ready for review. It is a small iteration cycle during which the development team delivers potentially shippable product increments.

### 13. Give the three principal roles in a scrum team. Explain their main responsibilities.
1. **Product Owner**: Responsible for defining the product backlog, prioritizing features, and ensuring the development team delivers value to stakeholders.
2. **Scrum Master**: Ensures that the Scrum framework is being followed, helps remove obstacles, and facilitates communication between the team and the Product Owner.
3. **Development Team**: Consists of developers who work together to deliver the features in the sprint backlog.

### 14. Draw a UML class diagram modeling marriages in various cultures:
- **Monogamy**: One wife to one husband.
- **Polygamy**: Persons can be married to multiple other people.
- **Polyandry**: One woman can be married to multiple men.
- **Polygyny**: One man can be married to multiple women.

To represent this, I'll provide a brief description:
- Create a base **Person** class.
- Use relationships such as **spouse** or **partners** to model different marriage types.
- In monogamy, there should be an association linking **Person** to **Person** with a constraint limiting the number of spouses to 1.
- In polygamy, **Person** may have a list of **spouses**, with no limitation.
- Specific subclasses or attributes can be created for **polyandry** and **polygyny** to represent the multiple husband/wife relationships respectively.

Since I cannot draw directly, you can create this using a tool like Lucidchart or draw.io.

### 15. Draw a UML diagram that represents an object "o" which creates an account (balance initially zero), deposits 100$, and then checks whether the balance is correct:
- Create a **Class Diagram** representing:
  - **Account** with attributes like `balance`.
  - **Operations** such as `createAccount()`, `deposit(amount)`, and `getBalance()`.
- Use an **Object Diagram** to instantiate an **Account** object `o` that shows an initial `balance = 0`, then show a **message** or action `deposit(100)` and a subsequent check of `getBalance()` returning `100`.
