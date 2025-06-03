## Describe the two types of coupled logical architectures that a distributed system may follow. Indicate the strengths and weaknesses of each of these types.

In distributed systems, two primary types of coupled logical architectures are layered and object-based architectures.

**Layered Architecture:**

- In a layered architecture, the system is organized into distinct layers, each with specific responsibilities. Each layer interacts only with the layers directly above and below it.
- **Strengths:**
  - Reduced number of interfaces, dependencies
  - Easy replacement of a layer
- **Weaknesses:**
  - Possible duplication of functionality

**Object-Based Architecture:**

- In an object-based architecture, the system is organized around objects that encapsulate both data and behavior. Objects communicate with each other through method invocations.
- **Strengths:**
  - No predefined interaction pattern
  - Highly flexible
- **Weaknesses:**
  - Complex to manage and maintain

## Describe the two types of decoupled logical architectures that a distributed system may follow. Indicate the strengths and weaknesses of each of these types.

In distributed systems, two primary types of decoupled logical architectures are event-based and data-centric.

**Event-Based Architecture:**

- In an event-based architecture, components communicate through events in a "publish-subscribe" style.
- **Strengths:**
  - Loose coupling of components
  - Flexibility in adding/removing components
- **Weaknesses:**
  - Complexity in managing event flows
  - Potential for message loss if not handled properly

**Data-Centric Architecture:**

- In a data-centric architecture, components interact through a shared database.
- **Strengths:**
  - Loose coupling of components
  - Centralized data management
- **Weaknesses:**
  - Possible performance bottlenecks due to central database access
  - Locking issues can arise, leading to contention and delays
