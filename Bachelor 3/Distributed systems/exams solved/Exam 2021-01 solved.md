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

**In summary:**

- **Tightly coupled architectures** are fast and consistent but rigid and fragile.
- **Loosely coupled architectures** are flexible, scalable, and fault-tolerant but may suffer from overhead and complexity in synchronization.

## Q2: MIDDLEWARE

A) Indicate the main differences between Local Method Invocation and Remote Method Invocations from the point of view of the used reference, the access and the number of invocations that are required by the client machine (invoker).

### **1. Reference Used**

- **LMI**:
  - The client uses a **direct reference (pointer or object reference in memory)** to call the method.
  - This reference points to an object in the same address space (same process).

- **RMI**:
  - The client uses a **remote reference (stub/proxy)** that represents the object located in a different address space (often on a different machine).
  - This remote reference abstracts communication details (serialization, networking).

---

### **2. Access**

- **LMI**:
  - The method is invoked **directly and locally**.
  - The call is as fast as a normal function call since it involves only the local stack and registers.

- **RMI**:
  - The method invocation is **indirect and remote**.
  - Requires **marshalling** (packing arguments), **network transfer**, and **unmarshalling** (unpacking on the server side).
  - Involves communication layers (stubs, skeletons, transport protocols).

---

### **3. Number of Invocations Required by the Client**

- **LMI**:
  - **One invocation**: the client calls the method, and it directly executes in the target object.

- **RMI**:
  - **Multiple invocations behind the scenes**:
    1. Client invokes the stub method (local call).
    2. Stub sends the request over the network to the server (remote call).
    3. Server skeleton invokes the actual method.
    4. Result is sent back over the network.
    5. Stub returns the result to the client.

  → From the client’s perspective, it looks like **one call**, but internally, it requires **at least two communications (request + response)** across the network.

B) Indicate what is the role of the Proxy on the Remote Method Invocation process. Indicate how the Proxy and the Skeleton are related.

In **RMI (Remote Method Invocation)**, communication between a client and a remote object on a server is abstracted so that invoking a method on a remote object looks almost the same as invoking a local one. This is achieved using **Proxy (Stub)** and **Skeleton**.

### 1. **Role of the Proxy (Stub)**

- The **Proxy (also called Stub)** acts as a **local representative** of the remote object on the client side.
- It provides the **same interface** as the remote object, so the client doesn’t need to know whether it is invoking a local or remote method.
- Its main responsibilities are:
  - **Marshalling**: converting method parameters into a form suitable for network transmission.
  - **Sending requests** to the remote JVM where the actual object resides.
  - **Receiving responses** from the remote object and unmarshalling return values or exceptions.
- In short: The proxy hides all the complexity of remote communication, letting the client code remain simple.

### 2. **Role of the Skeleton**

- The **Skeleton** is located on the **server side**
- It receives requests from the stub (client proxy), **unmarshals the data**, invokes the actual method implementation on the remote object, and then **marshals the result** to send back.

### 3. **Relationship between Proxy (Stub) and Skeleton**

- The **Proxy (Stub)** and **Skeleton** work together as communication endpoints:
  - The **Stub** translates local method calls into remote requests.
  - The **Skeleton** receives these requests, executes the corresponding method on the real remote object, and returns the result.
- Together, they form a **bridge** between the client and the remote object, making remote invocations appear as if they were local calls.

## Q3: SERVICE-ORIENTED ARCHITECTURES / CLOUD COMPUTING

A) Indicate the difference between the different types of multi-tenancy.

Data multi-tenancy focuses on how the **data is stored and segregated** for multiple tenants within a single software instance.

Application multi-tenancy focuses on how the **software application instance is shared** among tenants.

- **Data multi-tenancy:** Multiple tenants use the same application, but their data is stored separately. Isolation is at the **data level**.

- **Application multi-tenancy:** Multiple tenants share the same application and data structure. Isolation is at the **application level**, often with shared configurations.

B) List and describe the three service models commonly used in cloud computing. Provide an example of a service following each of the three models.

- **Infrastructure as a Service (IaaS)**: provides virtualized computing resources over the internet, such as virtual machines, storage, and networking. Example: AWS
- **Platform as a Service (PaaS)**: provides a platform allowing customers to develop, run, and manage applications without dealing with the underlying infrastructure. Example: Google App Engine
- **Software as a Service (SaaS)**: provides access to software applications over the internet, typically through a web browser, eliminating the need for local installation and maintenance. Example: Gmail

## Q4: WEB SERVICES

A) REST architectures are characterized by several architectural constraints. Explain each of the following constraints and indicate why each of them is desirable.
a) Client-server model, b) Caching and c) Layering

**a) Client-Server Model**

- **Explanation:** Separates the client (user interface) from the server (data storage and processing).
- **Desirability:** Promotes modularity, simplifies development, allows clients and servers to evolve independently, and improves scalability.

**b) Caching**

- **Explanation:** Responses can be marked as cacheable or non-cacheable so clients or intermediaries can store them for reuse.
- **Desirability:** Reduces latency, decreases server load, and improves network efficiency.

**c) Layering**

- **Explanation:** System is composed of hierarchical layers, where each layer only interacts with its immediate neighbors.
- **Desirability:** Enhances scalability, allows intermediaries like proxies or gateways, and improves security by encapsulating layers.

B) Describe five ways in which REST resources are described from the point of view of REST URI design.

1. Use nouns to represent resources (e.g., /users, /orders)
2. Use plural nouns for collections (e.g., /users)
3. Use hierarchical structure to represent relationships (e.g., /users/{userId}/orders)
4. Use query parameters for filtering, sorting, and pagination (e.g., /users?age=30&sort=name)
5. Use standard HTTP methods: GET (retrieve), POST (create), PUT (update), DELETE (remove), PATCH (partial update)
6. Permanent URIs: URIs should be stable and not change over time

## Q5: MICROSERVICES

A) The Reactive Manifesto is characterized by four architectural traits. Describe each of these traits and indicate their importance.

- **Responsive**: system responds in a timely manner
- **Resilient**: system remains responsive in the face of failure
- **Elastic**: system stays responsive under varying workload
- **Message-driven**: system relies on asynchronous message-passing to establish boundaries between components

B) Indicate why containers are considered a preferable solution over virtual machines (VM) for the implementations of microservices. Indicate at least one advantages and one disadvantage of using containers.

Containers are preferred over virtual machines for microservices because they are **lighter and faster**, sharing the host OS rather than running a full OS per instance, which enables **quick deployment and efficient resource use**.

- **Advantage:** Faster startup times and lower resource overhead.
- **Disadvantage:** Weaker isolation and security compared to VMs.

## Q6: DISTRIBUTED STORAGE

A) Directed Acyclic Graphs (DAGs) have been proposed as a good structure to handle distributed storage and processing. Indicate how these DAG structures are defined in the context of distributed storage and processing and what are the advantages of following this type of structure.

A **Directed Acyclic Graph (DAG)** is a graph of **nodes** (tasks or data blocks) and **directed edges** (dependencies), with no cycles.

- **In distributed storage:** DAGs represent how data blocks are encoded, replicated, and reconstructed.
- **In distributed processing:** DAGs represent computation tasks and their data dependencies, enabling scheduling and execution.

### **Advantages**

1. **Dependency tracking:** Clear order of tasks/data.
2. **Parallelism:** Independent tasks execute simultaneously.
3. **Fault tolerance:** Only affected tasks are recomputed.
4. **Scalability:** Efficient workload distribution.
5. **Optimized execution:** Reduces redundant computation.
6. **Determinism:** Predictable, consistent results.

B) Indicate the main difference between Narrow and Wide transformation in Resilient Distributed Datasets (RDDs). DataFrames.

**Main difference:**

- **Narrow transformation:** Each input partition maps to **one output partition**; no shuffle.
  _Examples:_ `map()`, `filter()` (RDDs); `select()`, `where()` (DataFrames)
- **Wide transformation:** Each input partition can map to **multiple output partitions**; involves **shuffle**.
  _Examples:_ `groupByKey()`, `join()` (RDDs); `groupBy().agg()`, `join()` (DataFrames)

## Q7: COORDINATION

A) Describe the Ricart-Agrawala algorithm and indicate how it compares with respect to the Ring-based algorithm.

The **Ricart-Agrawala algorithm** is a distributed mutual exclusion protocol where a process requests access to a critical section (CS) by sending a timestamped **REQUEST** message to all other processes. Each recipient replies immediately with a **REPLY** if it is not interested in the CS or defers the reply if it is. A process enters the CS only after receiving **REPLY** messages from all other processes. After exiting the CS, it sends any deferred replies.

**Comparison with Ring-based algorithm:**

| Feature            | Ricart-Agrawala                                                        | Ring-based                              |
| ------------------ | ---------------------------------------------------------------------- | --------------------------------------- |
| Message complexity | 2(N−1) per CS entry                                                    | N per CS entry                          |
| Fault tolerance    | Can handle failures but may block if a process crashes before replying | Token loss requires recovery mechanism  |
| Structure          | Fully distributed (no logical topology needed)                         | Logical ring required                   |
| Latency            | Depends on message delays from all processes                           | Depends on token circulation time       |
| Concurrency        | Multiple requests handled via timestamps                               | Only one token moves, sequential access |

**Summary:** Ricart-Agrawala is more message-intensive but simpler and fully distributed, while Ring-based is orderly, low-overhead per CS entry, but sensitive to token loss.

B) Describe the Garcia-Molina (Bully) algorithm and indicate how it compares with respect to the Chang-Roberts Ring-based algorithm.

The **Garcia-Molina (Bully) algorithm** is a **leader election algorithm** in distributed systems. Its key points:

1. Each process has a unique ID.
2. When a process notices the coordinator (leader) has failed, it **initiates an election** by sending an **ELECTION**message to all higher-ID processes.
3. If no higher-ID process responds, it **declares itself the coordinator** and broadcasts a **COORDINATOR** message.
4. If a higher-ID process responds, that process takes over the election.

**Comparison with Chang-Roberts Ring-based algorithm:**

| Feature            | Bully Algorithm                                                      | Chang-Roberts (Ring)                                                               |
| ------------------ | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Message complexity | O(N2) in worst case                                                  | O(N)                                                                               |
| Structure          | Fully connected (any process can contact any other)                  | Logical ring topology required                                                     |
| Fault tolerance    | Works if failures are detected; higher-ID process “bully” takes over | Works as long as token circulates; can recover from failures with extra mechanisms |
| Latency            | Faster if high-ID process is alive                                   | Sequential, slower for large rings                                                 |
| Concurrency        | Multiple elections may be started, resolved by ID                    | Only one election circulates at a time                                             |

**Summary:** Bully is faster in small networks and uses process IDs to resolve elections quickly but has higher message overhead. Ring-based is simpler and message-efficient for large rings but slower due to sequential propagation.

## Q8: REPLICATION

A) Describe the data-centric and client-centric consistency models.
Indicate what are the main advantages and disadvantages of using one over the other.

**1. Data-Centric Consistency**

- **Definition:** Consistency is defined from the system’s perspective; all replicas of a data item follow specific rules (e.g., sequential, causal, or eventual consistency).
- **Advantages:**
  - Guarantees predictable behavior across all clients.
  - Easier to reason about correctness in distributed systems.

- **Disadvantages:**
  - Can incur high latency or reduce availability to maintain strict consistency.
  - Less flexible for diverse client requirements.

**2. Client-Centric Consistency**

- **Definition:** Consistency is defined from the client’s perspective; each client sees a coherent view of data, even if replicas differ temporarily. Examples: _monotonic reads, read-your-writes_.
- **Advantages:**
  - Improves user experience by ensuring each client sees a consistent view.
  - Allows higher availability and lower latency since system-wide strict consistency is not required.

- **Disadvantages:**
  - No global consistency guarantees; different clients may see different data.
  - Harder to reason about system-wide correctness.

In short: **data-centric** ensures system-wide consistency; **client-centric** ensures consistency per client, trading global uniformity for better responsiveness.

B) Describe the Pipelined Random Access Memory (PRAM) consistency model. Indicate and justify whether the processes below follow the PRAM consistency model.

The **Pipelined Random Access Memory (PRAM)** consistency model is a **weak memory consistency model** for shared memory systems. Its key rules are:

- **Writes from a single process are seen in order by all other processes.** That is, if a process performs `W1` then `W2`, all other processes must see `W1` before `W2`.
- **Writes from different processes can be seen in different orders by different processes.** There is no guarantee of a global order across multiple processes.

PRAM focuses on **preserving program order per process**, but not inter-process order.

Suppose we have two processes:

**P1:** `W(X)=1; W(Y)=1`
**P2:** `R(Y); R(X)`

1. **If P2 reads `Y=1` then `X=1`:** ✅ Consistent with PRAM, because P1’s writes are observed in order.
2. **If P2 reads `Y=1` then `X=0`:** ❌ Violates PRAM, because it observes P1’s writes out of order.

In short: PRAM consistency **allows different processes to see writes from other processes in different orders**, but **never sees writes from the same process out of order**.
