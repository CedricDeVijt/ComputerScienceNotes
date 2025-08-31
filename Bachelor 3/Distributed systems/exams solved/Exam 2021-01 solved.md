## Q1: DISTRIBUTED SYSTEMS

A) Describe the two types of coupled logical architectures that a distributed system may follow. Indicate the strengths and weaknesses of each of these types.

In distributed systems, **coupled logical architectures** describe how different components (processes, services, or modules) depend on and interact with one another. Two main types of coupling are generally identified:

### 1. **Tightly Coupled Logical Architecture**

- **Description:**
  - Components are highly interdependent.

  - They share resources (such as memory or databases) and typically run under a single control mechanism.

  - Communication is often synchronous (e.g., direct function calls, RPC).

- **Strengths:**
  - **Performance efficiency:** Since components communicate directly, latency is low.

  - **Simpler coordination:** Easier to enforce consistency because everything is centrally controlled.

  - **Resource sharing:** Direct access to shared memory or state allows fast data exchange.

- **Weaknesses:**
  - **Scalability issues:** Scaling requires duplicating the entire system or making complex adjustments.

  - **Reduced fault tolerance:** A failure in one component can propagate and crash the whole system.

  - **Limited flexibility:** Hard to modify or replace individual components without affecting the rest.

### 2. **Loosely Coupled Logical Architecture**

- **Description:**
  - Components are relatively independent and interact via message passing, middleware, or APIs.

  - Communication is often asynchronous, and each component manages its own resources.

- **Strengths:**
  - **High scalability:** New components can be added without major redesign.

  - **Fault tolerance:** Failures in one component are less likely to bring down the entire system.

  - **Flexibility and maintainability:** Components can be developed, updated, or replaced independently.

  - **Heterogeneity support:** Different technologies, platforms, or programming languages can coexist.

- **Weaknesses:**
  - **Higher communication overhead:** Message passing and middleware introduce latency.

  - **Complexity of coordination:** Ensuring consistency across independent components is harder.

  - **Potential reliability concerns:** Network failures or message loss must be handled explicitly.

✅ **In summary:**

- **Tightly coupled architectures** are fast and consistent but rigid and fragile.

- **Loosely coupled architectures** are flexible, scalable, and fault-tolerant but may suffer from overhead and complexity in synchronization.

Do you want me to also give you a **real-world example** (like how this applies to microservices vs monolithic systems) so it’s easier to visualize?

## Q2: MIDDLEWARE

A) Indicate the main differences between Local Method Invocation and Remote Method Invocations from the point of view of the used reference, the access and the number of invocations that are required by the client machine (invoker).

B) Indicate what is the role of the Proxy on the Remote Method Invocation process. Indicate how the Proxy and the Skeleton are related.

## Q3: SERVICE-ORIENTED ARCHITECTURES / CLOUD COMPUTING

A) Indicate the difference between the different types of multi-tenancy.

B) List and describe the three service models commonly used in cloud computing. Provide an example of a service following each of the three models.

## Q4: WEB SERVICES

A) REST architectures are characterized by several architectural constraints. Explain each of the following constraints and indicate why each of them is desirable.
a) Client-server model, b) Caching and c) Layering

B) Describe five ways in which REST resources are described from the point of view of REST URI design.

## Q5: MICROSERVICES

A) The Reactive Manifesto is characterized by four architectural traits. Describe each of these traits and indicate their importance.

B) Indicate why containers are considered a preferable solution over virtual machines (VM) for the implementations of microservices. Indicate at least one advantages and one disadvantage of using containers.

## Q6: DISTRIBUTED STORAGE

A) Directed Acyclic Graphs (DAGs) have been proposed as a good structure to handle distributed storage and processing. Indicate how these DAG structures are defined in the context of distributed storage and processing and what are the advantages of following this type of structure.

B) Indicate the main difference between Narrow and Wide transformation in Resilient Distributed Datasets (RDDs). DataFrames.

## Q7: COORDINATION

A) Describe the Ricart-Agrawala algorithm and indicate how it compares with respect to the Ring-based algorithm.

B) Describe the Garcia-Molina (Bully) algorithm and indicate how it compares with respect to the Chang-Roberts Ring-based algorithm.

## Q8: REPLICATION

A) Describe the data-centric and client-centric consistency models.
Indicate what are the main advantages and disadvantages of using one over the other.

B) Describe the Pipelined Random Access Memory (PRAM) consistency model. Indicate and justify whether the processes below follow the PRAM consistency model.
