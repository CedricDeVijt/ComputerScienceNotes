## 8.1: Introduction to Domain Modeling
- **Purpose of Domain Modeling**: Validates and analyzes requirements to confirm that we understand the problem domain and that we are building the correct system.
- **Challenges**:
  - **Customer Ambiguity**: Customers often lack clarity or change their requirements.
  - **Adaptability**: Use cases and requirements can evolve over time, necessitating flexible models that focus on *what* rather than *how* a process is done.

## 8.2: CRC (Class-Responsibility-Collaboration) Cards
- **Definition**: CRC cards are used to model domain concepts by defining classes, their responsibilities, and collaborations.
- **Benefits**:
  - Compact, manipulable, and easy to modify or discard.
  - Encourages brainstorming and role-play, aiding in problem decomposition and responsibility-driven design.
- **Key Components**:
  - **Class**: Defined with name, superclasses, subclasses.
  - **Responsibilities**: Functions each class must perform.
  - **Collaborations**: Other classes required to fulfill responsibilities.

![[Pasted image 20241112140604.png]]

## 8.3: Problem Decomposition
- **Functional vs. Object-Oriented Decomposition**:
  - **Functional**:
    - Centralized responsibilities, stable for single-function systems.
    - Susceptible to maintainability issues as requirements evolve.
  - **Object-Oriented**:
    - Distributed responsibilities, encapsulation, and flexibility in complex systems.
    - Suitable for dynamic requirements due to the modularity of objects.

![[Pasted image 20241112140913.png]]

![[Pasted image 20241112140929.png]]

## 8.4: Identifying Objects and Responsibilities
- **Object Identification Techniques**:
  - **Noun and Verb Phrase Analysis**: Nouns often suggest objects, while verbs indicate responsibilities.
  - **Class Enumeration and Role Definition**: List and organize potential classes and their interactions.
- **Responsibilities and Collaborations**:
  - Defined as services provided by objects, not how they are implemented.
  - Collaborations represent the relationships or dependencies between objects.

## 8.5: Hierarchies in Domain Modeling
- **Hierarchical Organization**:
  - **Liskov Substitution Principle**: Ensures subclasses can replace superclasses without issue.
  - **Guidelines**:
    - Avoid deep and narrow hierarchies; classes should not exceed six superclasses.
    - Factor out common responsibilities and strive for shallow, broad hierarchies.

## 8.6: Feature Models and Product Lines
- **Feature Models**: Visual representations of features, showing commonalities and variations in product lines.
  - **Feature Diagram Components**:
    - **Mandatory Features**: Essential for all product variations.
    - **Optional Features**: Available but not required in all variations.
    - **Alternative Features**: Mutually exclusive options.
- **Product Lines**:
  - **Definition**: A family of related products designed to leverage shared features and variabilities.
  - **Example**: Linux kernel with configurable features allows for customized variants.

## 8.7: Clone-and-Own Approach
- **Definition**: Creating a new product variant by copying and modifying an existing one.
- **Advantages**:
  - Time efficiency and independence in production.
  - Reduces costs for new variants.
- **Drawbacks**:
  - Maintenance challenges as changes need to propagate across clones.
  - Risk of duplicated efforts and bugs across variants.

## 8.8: Social Coding and Variant Forks
- **Social Forks**: Temporary forks for development, patches, and features, often merged back into the main project.
- **Variant Forks**: Permanent, maintained separately to meet specific requirements, resulting in divergent development paths.

## 8.9: Ensuring Correctness and Traceability
- **Correctness**: Ensures that models are accurate and address the actual needs of the customer.
  - Achieved through scenario walkthroughs and role-playing.
- **Traceability**:
  - **Requirements Traceability**: Maintaining alignment between requirements and system models, especially through proper naming conventions.
  - **Feature Diagrams**: Aid in mapping requirements by making distinctions between product variations clear.

---

## Key Points to Remember
- **Domain Modeling** is essential to validate and capture requirements accurately.
- **CRC Cards** facilitate brainstorming by assigning responsibilities and collaborators to objects.
- **Object-Oriented Decomposition** is preferable for systems with evolving requirements due to its flexibility and encapsulation.
- **Functional Decomposition** is suitable for systems with stable, singular functions but struggles with evolving requirements.
- **Feature Models** help map product lines, distinguishing mandatory, optional, and alternative features.
- **Clone-and-Own Approach** benefits short-term efficiency but can complicate long-term maintenance.
- **Social Coding Forks vs. Variant Forks**: Social forks are temporary and collaborative, while variant forks serve distinct, long-term needs.
- **Correctness and Traceability** are achieved through proper documentation, role-play scenarios, and systematic feature mapping.