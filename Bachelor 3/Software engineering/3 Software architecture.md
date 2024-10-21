# 3.1 Introduction to Software Architecture

### 3.1.1 When, Why, and What?
- **Software architecture** is necessary for large-scale systems to organize work in development teams.
- **Conway’s Law**: "Organizations designing systems are constrained to produce designs reflecting their communication structures."
  
### 3.1.2 Functional vs. Non-functional Requirements
- **Functional requirements**: What the system **does** (features, capabilities).
- **Non-functional requirements**: Constraints like **performance**, **maintainability**, and **usability**.

### 3.1.3 Coupling and Cohesion
- **Coupling**: Measure of how tightly components are connected.
- **Cohesion**: How well the elements within a component work together.
  - Aim: Minimize coupling, maximize cohesion.

### 3.1.4 Patterns
- **Pattern**: The essence of a solution to a recurring problem in a particular context
- **Pattern Form**: usually written down following a semi-structured template. They have a name and allow experts to have deep design discussions in a few words
# 3.2 Macro Architectures

### 3.2.1 Layered Architecture
- Layers separate **concerns**: each layer provides services to the one above and accesses the one below.

![[Pasted image 20241021110428.png]]
### 3.2.2 Pipes and Filters
- System is divided into **filters** that process data streams and **pipes** that connect them.
  - **Example**: UNIX commands, CGI scripts for web forms.

``` UNIX
tar cf - .| gzip -cfbest| rsh hcoss dd
```
  
### 3.2.3 Blackboard Architecture
- Central repository (**blackboard**) with several **knowledge sources** that modify it.
  - Used for complex systems requiring partial solutions.

![[Pasted image 20241021110306.png]]
  
### 3.2.4 Model-View-Controller (MVC)
- **Model**: provides functional core (data)
	- registers dependent views/controllers
	- notifies dependent components about changes (send update)
- **View**: creates and initializes associated controller + displays information
	+ responds to notification events (receive update)
- **Controller**: accepts user input events + translate events into requests to model and view
	+ responds to notification events (receive update)

- Used in **interactive applications**.

# 3.3 Micro Architectures

### 3.3.1 Observer Pattern
- Decouple an object (subject) from its dependents (observers).
  - **Subject** notifies observers when a change occurs.
  
### 3.3.2 Abstract Factory
- Provides an interface for creating **families of related objects** without specifying their concrete classes.
  
### 3.3.3 Adapter (Wrapper)
- Converts an interface into another one that a client expects.


# 3.4 Other Patterns

### 3.4.1 Security Patterns: Single Access Point
- Ensure system integrity by defining a **single entry point** for external access.

### 3.4.2 Microservices
- System is divided into **small, loosely coupled services**.
  - Each service corresponds to a specific **business functionality**.
  - Benefits: **scalability**, **independent deployment**.


# 3.5 Architecture Evaluation

### 3.5.1 Architecture Tradeoff Analysis Method (ATAM)
- Evaluates risks and trade-offs between competing architectural decisions.
  - Focuses on **sensitivity points** (components critical to quality) and **tradeoff points** (conflicting qualities).

![[Pasted image 20241021115057.png]]

### 3.5.2 Architecture in SCRUM
- **Spike**: A short experiment to test architectural alternatives.
- **Architecture Runway**: Extends architecture incrementally to accommodate future functionality.


# 3.6 Correctness and Traceability

- **Correctness**: Ensures the architecture addresses **non-functional requirements**.
- **Traceability**: The ability to trace from **requirements to architecture** and implementation.


# Key Points to Remember

- **Software architecture** is the blueprint for both the system and project development.
- **Conway's Law** links organization structure with system design.
- **Functional requirements** define what a system does, while **non-functional** ones handle quality attributes.
- The balance between **coupling** (low) and **cohesion** (high) is critical for a good design.
- **Layered architectures** separate different levels of abstraction.
- **Pipes and filters** are ideal for **data stream** processing.
- **Observer pattern** allows for a change in one object to be reflected in others.
- **Abstract factory** aids in the creation of related objects without specifying the exact classes.
- **Microservices** enable systems to scale and deploy independently by dividing them into smaller services.
- **ATAM** is crucial for assessing architectural risks and trade-offs.
- **Spikes** in SCRUM help prototype architectural decisions.
- **Guardrails** ensure teams stay within the agreed-upon boundaries of design and development practices.