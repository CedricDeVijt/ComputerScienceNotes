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

## Describe the two types of system architectures that a distributed system may follow. Indicate the strengths and weaknesses of each of these types.

In distributed systems, two primary types of system architectures are client-server and peer-to-peer architectures.
**Client-Server Architecture:**

- In a client-server architecture, clients request services from centralized servers that provide those services.
- **Strengths:**

  - Centralized control and management
  - Easier to implement security measures

- **Weaknesses:**
  - Single point of failure (if the server goes down, clients cannot access services)
  - Scalability issues as the number of clients increases

**Peer-to-Peer Architecture:**

- In a peer-to-peer architecture, all nodes (peers) in the network can act as both clients and servers, sharing resources directly with each other.
- **Strengths:**
  - No single point of failure (if one peer goes down, others can still function)
  - Better scalability as resources are distributed across peers
- **Weaknesses:**
  - More complex to manage and maintain
  - Security can be more challenging, as there is no centralized control
