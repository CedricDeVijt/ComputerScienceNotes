# 1 Introduction

## Definitions

- **Service**: part of a computer system managing a collection of related resources, presenting their functionality to users and applications.
- **server**: a running program (a process) that accepts requests from programs running on other computers (clients) to perform a service, and responds appropriately.
- **client**: running process on networked computer sending service requests to server.
- **remote invocation**: complete interaction between client and server to process single request.

## Motivation

- Cost: cheaper to use many low-cost systems than one high-end system.
- Capability: some problems too large for single system (memory, data storage, computational requirements).
- Concurrency: many problems have inherent options for parallelism.
- Reliability: distributing redundant components minimizes probability faults impact user.
- Integration: for organizations to interact, their systems need to interact.
- Distribution: many applications inherently distributed as users are geographically spread (e.g. email, WWW).

## Challenges

- Heterogeneity: different hardware, OS, programming languages, network technologies.
- Openness: systems need to be extensible and support new services, protocols, etc.
- Security: need to protect data and resources from unauthorized access and attacks.
- Scalability: system must work efficiently as it grows in size and complexity.
- Fault tolerance: system must continue to operate despite failures of components.
- Transparency: hide complexity of distributed system from users and applications.

## Distributed system architectures

### Logical architecture styles

#### Coupled architectures

- tightly coupled systems with high degree of interdependence
- Adding/removing a component is non-trivial

**Layered architecture**

- system organized into layers, each providing services to layer above and using services of layer below

Pros:

- easy replacement of a layer
- reduced number of interfaces, dependencies

Cons:

- possible duplication of functionality

**Oject-based architecture**

- system organized around objects that encapsulate data and behavior
- objects communicate via method invocations

Pros:

- no predefined interaction pattern
- highly flexible

Cons:

- complex to manage and maintain

#### Decoupled architectures

- loosely coupled systems with low degree of interdependence
- Adding/removing a component is easy

**Event-based architecture**

- components communicate by producing and consuming events

Pros:

- loose coupling of components
- high scalability

Cons:

- complex event management

**Data-centric architecture**

- components share a common data store

Pros:

- simplified data sharing
- easier data management

Cons:

- potential bottleneck at data store
- complex data consistency management

## Client server architectures

- clients request services from servers
- servers provide services to clients

**"simple" client-server architecture**: clients directly communicate with servers
**client-multiserver architecture** (explicit server lookup): clients communicate with multiple servers, often via a directory service
**client-multiserver architecture** (implicit server lookup): clients communicate with multiple servers, often via a load balancer
**proxy architecture**: clients communicate with servers via a proxy that forwards requests and responses

## Peer-to-peer architectures

- all nodes are equal and can act as both clients and servers
- nodes communicate directly with each other

# 2 Middleware and Communication

## Achieve basic communication

- Berkeley socket
- Socket pair described by 4 -tuple (source IP, source port, dest IP, dest port)

## Why middleware?

- Role of middleware: Hide complexity of network communication, provide standard communication patterns, enable focus on application logic rather than infrastructure BUT programmer should know object is remote

- Remote object references: local object that represents a remote object, allowing clients to invoke methods on remote objects as if they were local

- local/remote method invocations: local method invocations are direct calls to methods on local objects, while remote method invocations involve communication over a network to invoke methods on remote objects

### Fault tolerances

1. **Retry**: automatically retry failed operations a certain number of times before giving up
2. **Duplicate filtering**: detect and discard duplicate messages to prevent processing the same request multiple times
3. **Retransmission**: resend lost or corrupted messages to ensure reliable communication
   3.1 Re-execution: re-execute operations that may have failed due to transient errors
   3.2 Retransmit old reply: resend previous responses to clients if the original response was lost

### Invocation semantics

What guarantees are given on the number of executions of remote method invocations?

| Semantic          | Retransmit request message | Duplicate filtering | Re-execute procedure or retransmit reply |
| ----------------- | -------------------------- | ------------------- | ---------------------------------------- |
| **Maybe**         | No                         | Not applicable      | Not applicable                           |
| **At-least-once** | Yes                        | No                  | Re-execute procedure                     |
| **At-most-once**  | Yes                        | Yes                 | Retransmit old reply                     |

## Middleware architecture

### Proxy

- Client-side component that represents the remote object
- Marshals method calls into network messages
- Sends request messages to the server

### Skeleton

- Server-side component that receives network messages, acts like the local invoker to the object
- Unmarshals messages into method calls on the actual remote object
- Sends reply messages back to the client

### Marshalling/Unmarshalling

- Process of converting objects to/from byte streams for network transmission
- Standards: Java Serialization, Protocol Buffers (Google), CORBA CDR

### Communication modules

1. Client invoces method
2. Proxy marshals request into message
3. Message sent over network
4. Skeleton receives message
5. Skeleton unmarshals message into method call
6. Method executed on server
7. Result marshaled into reply message
8. Reply message sent over network
9. Proxy receives reply message
10. Proxy unmarshals reply message into result
11. Client receives result

**Dispatcher**: Component that receives incoming messages and routes them to the appropriate skeleton based on the target object

**Remote reference module**: Responsible for managing remote object references, including creating, storing, and looking up references to remote objects
**Binding service**: Provides a way for clients to discover and obtain references to remote objects, often through a directory or naming service

# 3 Service-Oriented Architectures

**Service**: self-contained unit of functionality that exposes its capabilities through a well-defined interface, can be independently deployed and managed, and is designed to be reusable and composable with other services.

**Service-oriented architecture (SOA)**: architectural style that structures applications as a collection of loosely coupled services that communicate over a network, often defined in terms of contracts, focuses on shared, reusable and loosely coupled services.

**Architecture**: set of principles and guidelines for designing and building software systems, including components, their interactions, and the overall structure of the system.

## Multi-tenancy

- single instance of software serves multiple customers (tenants)
- each tenant's data is isolated and remains invisible to other tenants

- **Data multitenancy**: multiple tenants share the same database schema, with tenant-specific data identified by a tenant ID
- **Application multitenancy**: each tenant has its own instance of the application, allowing for greater customization and isolation

## Cloud computing

Cloud computing is a model for enabling convenient, on-demand network access to a shared pool of configurable computing resources

## X as a Service (XaaS)

- **Infrastructure as a Service (IaaS)**: provides virtualized computing resources over the internet, such as virtual machines, storage, and networking
- **Platform as a Service (PaaS)**: provides a platform allowing customers to develop, run, and manage applications without dealing with the underlying infrastructure
- **Software as a Service (SaaS)**: provides access to software applications over the internet, typically through a web browser, eliminating the need for local installation and maintenance

Examples:

- IaaS: Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP)
- PaaS: Heroku, Google App Engine, Microsoft Azure App Service
- SaaS: Google Workspace (Gmail, Docs), Microsoft 365, Salesforce

## Payment models

1. **Per-instance**: pay for each instance of a service used
2. **Reserved**: pay upfront for a reserved capacity of a service
3. **Bidding**: bid for unused capacity of a service at a lower price
4. **Metered**: pay based on actual usage of a service (e.g., compute hours, storage used)

# 4 Web Services

**Web service**: software system designed to support interoperable machine-to-machine interaction over a network, typically using standard protocols such as HTTP and data formats like XML or JSON.

## Web services in theory and practice

Benefits of web services:

- Loose coupling: services can be developed, deployed, and maintained independently
- Ease of integration: standard protocols and data formats facilitate integration between different systems
- Reusability: services can be reused across different applications and contexts
- Interoperability: web services can communicate across different platforms and programming languages

## RESTful Web Services

**REST (Representational State Transfer)**: architectural style for designing networked applications, emphasizing stateless communication, resource-based interactions, and the use of standard HTTP methods.

Principles of REST (Architectural constraints):

1. **Uniform Interface**: a consistent and standardized way of interacting with resources, typically using standard HTTP methods and URIs.
2. **Client-Server Architecture**: separation of concerns between client and server, allowing them to evolve independently.
3. **Statelessness**: each request from client to server must contain all the information needed to understand and process the request, and the server should not store any client context between requests.
4. **Cacheability**: responses from the server can be marked as cacheable or non-cacheable, allowing clients to cache responses and improve performance.
5. **Layered System**: the architecture can be composed of multiple layers, with each layer only interacting with the layer directly above or below it, enhancing scalability and manageability.
6. **Code on Demand (optional)**: servers can temporarily extend or customize the functionality of a client by transferring executable code (e.g., JavaScript).

URI design:

- Use nouns to represent resources (e.g., /users, /orders)
- Use plural nouns for collections (e.g., /users)
- Use hierarchical structure to represent relationships (e.g., /users/{userId}/orders)
- Use query parameters for filtering, sorting, and pagination (e.g., /users?age=30&sort=name)
- Use standard HTTP methods: GET (retrieve), POST (create), PUT (update), DELETE (remove), PATCH (partial update)
- Permanent URIs: URIs should be stable and not change over time

## REST vs RPC

RPC:

- many operations, few uri
- addres software components
- procedrure name and parameters are transferred

REST:

- few operations, many uri
- address resources
- resource state is transferred

## SOAP Web Services

**SOAP (Simple Object Access Protocol)**: protocol for exchanging structured information in web services, using XML as the message format and typically relying on HTTP or SMTP for message transmission.

## REST vs SOAP

| Feature      | REST                                                  | SOAP                                              |
| ------------ | ----------------------------------------------------- | ------------------------------------------------- |
| Protocol     | Uses standard HTTP methods (GET, POST, PUT, DELETE)   | Uses specific SOAP protocol over HTTP, SMTP, etc. |
| Messaging    | Resource-based, stateless communication               | Operation-based, can be stateful                  |
| Statefulness | Stateless                                             | Can be stateful or stateless                      |
| Performance  | Generally faster due to lightweight nature            | Can be slower due to XML processing               |
| Flexibility  | More flexible, can use multiple data formats          | Less flexible, strictly XML-based                 |
| Standards    | No strict standards, more architectural style         | Strict standards defined by W3C                   |
| Security     | Relies on underlying transport security (e.g., HTTPS) | Built-in security features (WS-Security)          |
| Complexity   | Simpler to implement and use                          | More complex due to strict standards              |

Advantages of REST:

- Uniform interface is immutable
- Conceptually simpler
- Lower protocol overhead (for stateless services)
- Can improve server scalability
- Inherent support for request caching
- Less reliant on tool support and heavyweight libraries
- No need for additional messaging layer
- Complexity at the endpoints instead of the transport layer level

Advantages of SOAP:

- Standardized protocol with strict rules
- Built-in error handling and messaging patterns
- Supports complex operations and transactions
- Built-in security features (WS-Security)
- Language and platform independent
- Extensible through WS-\* standards (e.g., WS-Addressing, WS-ReliableMessaging)

## When to use which?

- Use REST for simple, lightweight, and scalable web services that require flexibility and performance.
- Use SOAP for complex, enterprise-level web services that require strict standards, built-in security, and transactional reliability.

## WSDL

**WSDL (Web Services Description Language)**: XML-based language for describing the functionality, operations, and message formats of a web service, allowing clients to understand how to interact with the service.

## Web Service VS Service Oriented Architecture

| Feature                | Web Service                                                       | Service-Oriented Architecture (SOA)                                                      |
| ---------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Definition             | Software system for machine-to-machine interaction over a network | Architectural style structuring applications as a collection of loosely coupled services |
| Communication Protocol | Typically uses HTTP, XML, JSON                                    | Can use various protocols (HTTP, JMS, etc.)                                              |
| Service Granularity    | Can be fine-grained or coarse-grained                             | Typically coarse-grained services                                                        |
| Interoperability       | High, due to standard protocols and formats                       | High, but depends on service design and implementation                                   |
| Reusability            | Services can be reused across different applications              | Emphasizes reuse of services across the enterprise                                       |
| Loose Coupling         | Yes, services are designed to be independent                      | Yes, services are loosely coupled                                                        |

# 5 Microservices

**Microservice architecture**: architectural style that structures an application as a collection of small, autonomous services modeled around a business domain, each service running in its own process and communicating with lightweight mechanisms, often HTTP-based APIs.

**Microservice**: small, independently deployable service that performs a specific business function, designed to be loosely coupled, highly maintainable, and scalable.

## Characteristics and design principles of microservices

1. **Single Responsibility Principle**: each microservice should focus on a single business capability or function.
2. **Independently Deployable**: microservices can be developed, tested, and
   deployed independently of each other.
3. **Decentralized Data Management**: each microservice manages its own database or data store, promoting data encapsulation and autonomy.
4. **Lightweight Communication**: microservices communicate using lightweight protocols, such as HTTP/REST or messaging queues.
5. **Polyglot Programming**: different microservices can be developed using different programming languages and technologies, allowing teams to choose the best tools for their specific needs.
6. **Automated Deployment**: continuous integration and continuous deployment (CI/CD) pipelines are essential for automating the deployment of microservices.
7. **Resilience and Fault Tolerance**: microservices should be designed to handle failures gracefully, using techniques such as circuit breakers and retries.
8. **Scalability**: microservices can be scaled independently based on demand, allowing for efficient resource utilization.
9. **Monitoring and Logging**: comprehensive monitoring and logging are crucial for managing and troubleshooting microservices in production environments.
10. **Organized Around Business Capabilities**: teams should be organized around business capabilities, with each team responsible for the full lifecycle of their microservices.

## Reactice Manifesto

- Responsive: system responds in a timely manner
- Resilient: system remains responsive in the face of failure
- Elastic: system stays responsive under varying workload
- Message-driven: system relies on asynchronous message-passing to establish boundaries between components

## Container technologies

**VM (Virtual Machine)**: software emulation of a physical computer that runs an operating system and applications, providing isolation and resource management.
**Container**: lightweight, portable, and self-contained environment that packages an application and its dependencies, allowing it to run consistently across different computing environments.

Pros of containers :

- Lightweight: share the host OS kernel, reducing overhead compared to VMs
- Fast startup: containers can start in seconds, while VMs may take minutes
- Portability: containers can run consistently across different environments
- Resource efficiency: multiple containers can run on a single host with minimal resource usage
- Simplified deployment: containers package applications and dependencies together

Cons of containers:

- Security: shared kernel can lead to potential vulnerabilities
- Isolation: containers provide less isolation than VMs
- Complexity: managing container orchestration can be complex
- Cannot run different OS: containers must use the same OS as the host

## Containers vs VMs

| Feature        | Virtual Machines (VMs)                       | Containers                                                |
| -------------- | -------------------------------------------- | --------------------------------------------------------- |
| Isolation      | Full OS-level isolation                      | Process-level isolation                                   |
| Resource Usage | Higher resource overhead due to full OS      | Lower resource overhead, shares host OS kernel            |
| Startup Time   | Slower, can take minutes to boot             | Faster, can start in seconds                              |
| Portability    | Less portable, tied to specific hypervisor   | More portable, can run on any host with container runtime |
| Management     | More complex, requires hypervisor management | Simpler, can use container orchestration tools            |
| Performance    | Generally slower due to OS overhead          | Generally faster due to lightweight nature                |
| OS Support     | Can run different OS on the same host        | Must use the same OS as the host                          |

## How containers enable microservices

- Isolation: containers provide isolated environments for each microservice, preventing conflicts and ensuring consistent behavior across different environments.
- Portability: containers can be easily moved between development, testing, and production environments, facilitating continuous integration and deployment (CI/CD) pipelines.
- Scalability: containers can be quickly scaled up or down based on demand, allowing microservices to handle varying workloads efficiently.
- Resource Efficiency: multiple containers can run on a single host with minimal resource usage, enabling cost-effective deployment of microservices.
- Simplified Deployment: containers package microservices and their dependencies together, simplifying the deployment process and reducing the risk of configuration issues.
- Consistency: containers ensure that microservices run consistently across different environments, reducing the "it

# 6 Distributed Storage Systems

**Distributed storage system**: system that manages data across multiple storage nodes, providing scalability, fault tolerance, and high availability.
**HDFS (Hadoop Distributed File System)**: distributed file system designed to run on commodity hardware, providing high throughput access to large datasets and fault tolerance through data replication.
**MapReduce**: programming model and processing technique for distributed computing, allowing large datasets to be processed in parallel across a cluster of computers.
**Spark**: distributed computing framework that provides in-memory processing capabilities, enabling fast and interactive data analysis.

## HDFS

1. Split files into large blocks (default 128MB)
2. Distribute blocks across cluster nodes (default 3 replicas)

When DataNode fails, NameNode re-replicates blocks to maintain desired replication level

## Hadoop MapReduce

1. **Split**: input data is split into fixed-size chunks (input splits)
2. **Map**: map function processes each input split, producing intermediate key-value pairs
3. **Shuffle and Sort**: intermediate key-value pairs are shuffled and sorted by key
4. **Reduce**: reduce function processes each group of intermediate values for a key, producing final output key-value pairs
5. **Output**: final output is written to distributed storage (e.g., HDFS)

## YARN

- ResourceManager: manages cluster resources and schedules applications
- NodeManager: manages resources and monitors application containers on each node
- ApplicationMaster: manages the lifecycle of a specific application, including resource requests and task scheduling

## Spark

- Works on top of Hadoop
- Has many other workflows (join, filter, groupByKey, etc.)
- In-memory caching of data for faster processing

- RDD (Resilient Distributed Dataset): immutable, distributed collection of objects that can be processed in parallel, providing fault tolerance through lineage information.

# 7 Replication

**Replication**: process of creating and maintaining multiple copies of data across different nodes in a distributed system, enhancing data availability, fault tolerance, and performance.
**Consistency model**: set of rules that define how and when updates to replicated data are visible to users and applications in a distributed system.
**Strong consistency**: guarantees that all replicas of a data item are immediately updated and consistent after a write operation, ensuring that any read operation returns the most recent write.
**Eventual consistency**: guarantees that, given enough time without new updates, all replicas of a data item will eventually converge to the same value, allowing for temporary inconsistencies.
**Causal consistency**: ensures that operations that are causally related are seen by all processes in the same order, while operations that are not causally related may be seen in different orders by different processes.

## Why replication?

1. **Fault tolerance**: replication ensures that data remains available even if some nodes fail.
2. **Improved performance**: replication can reduce latency and improve read performance by allowing data to be accessed from multiple locations.
3. **Load balancing**: replication can distribute read requests across multiple replicas, reducing the load on any single node.
4. **Data locality**: replication can place data closer to users, improving access times and reducing network congestion.

## CAP Theorem

In a distributed data store, it is impossible to simultaneously provide more than two out of the following three guarantees:

1. **Consistency**: all nodes see the same data at the same time
2. **Availability**: every request receives a response, without guarantee that it contains the most recent data
3. **Partition tolerance**: the system continues to operate despite arbitrary message loss or failure of part of the system

## Consistency models

### Data-centric consistency models

= Models that define the behavior of the system from the perspective of the data itself, focusing on how updates to replicated data are propagated and made visible to users and applications.

1. **Strict consistency**: every read operation returns the most recent write, as if there is a single copy of the data
2. **Sequential consistency**: all operations appear to be executed in some sequential order, and each process sees its own operations in the order they were issued
3. **Causal consistency**: operations that are causally related are seen by all processes in the same order
4. **PRAM (Pipelined Random Access Memory) consistency (FIFO)**: writes from a single process are seen by all processes in the order they were issued, but writes from different processes may be seen in different orders
5. **Weak consistency**: no guarantees about the order of operations or visibility of updates
6. **Release consistency**: updates are propagated to replicas only at specific synchronization points
7. **Entry consistency**: updates are propagated to replicas when a process enters a critical section

### Client-centric consistency models

= Models that define the behavior of the system from the perspective of individual clients, focusing on the guarantees provided to clients regarding the visibility of their own operations.

1. **Monotonic reads**: if a process reads a value, any subsequent reads by that process will return the same or a more recent value
2. **Monotonic writes**: if a process writes a value, any subsequent writes by that process will be based on the value it wrote or a more recent value
3. **Read your writes**: if a process writes a value, any subsequent reads by that process will return the value it wrote or a more recent value
4. **Writes follow reads**: if a process reads a value and then writes a new value, the write will be based on the value it read or a more recent value

### Trade-offs

Consistency and redundancy:

- All replicas must be updated for strong consistency, leading to higher latency and reduced availability during network partitions.
- All copies must contain full state
- Reduced consistency leads to reduced redundancy

Consistency and performance

- Consistency induces extra computation and communication
- Increased consistency leads to decreased performance

Consistency and scalability

- Scalability depends on the implementation of a consistency model
- Avoid centralized approaches
- Avoid strong increase in communication

# 8 Coordination

## Distributed Mutual Exclusion

### Central Algorithm

**How It Works**

- A single coordinator node manages access to a shared resource (e.g., for mutual exclusion).
- Nodes send requests to the coordinator, which grants access based on a queue or priority system.
- The coordinator ensures only one node accesses the resource at a time.

**Pros**

- **Simple**: Easy to implement and understand.
- **Deterministic**: Centralized control ensures predictable behavior.
- **Low message overhead**: Nodes only communicate with the coordinator.

**Cons**

- **Single point of failure**: If the coordinator fails, the system halts.
- **Scalability issues**: The coordinator can become a bottleneck in large systems.
- **High latency**: All requests must go through the coordinator, increasing delay in large networks.

### Ring-Based Algorithm

**How It Works**

- Nodes are organized in a logical ring topology.
- A token or message circulates around the ring. For mutual exclusion, only the node holding the token can access the shared resource.

**Pros**

- **Simple structure**: Easy to implement in systems with a ring topology.
- **Fairness**: Nodes get equal opportunity to access resources as the token circulates.
- **No central coordinator**: Avoids single point of failure.

**Cons**

- **High latency**: Token must traverse the entire ring, which can be slow in large systems.
- **Fault intolerance**: If a node fails, the ring breaks, disrupting the algorithm unless recovery mechanisms are in place.
- **Inefficient for sparse access**: If only a few nodes need the resource, the token still circulates through all nodes.

### Ricart-Agrawala Algorithm

**How It Works**

- A distributed mutual exclusion algorithm where nodes request access to a critical section by sending timestamped messages to all other nodes.
- A node grants permission to another node only if it is not in or requesting the critical section itself, using logical timestamps to resolve conflicts.
- A node enters the critical section only after receiving permission from all other nodes.

**Pros**

- **Decentralized**: No single point of failure.
- **Fairness**: Timestamps ensure requests are processed in order.
- **Robust**: Works in fully distributed systems without requiring a coordinator.

**Cons**

- **High message complexity**: Requires O(N) messages per request (N = number of nodes), leading to network overhead.
- **Latency**: Waiting for all permissions can be slow, especially in large systems.
- **Clock synchronization**: Relies on logical clocks, which may introduce complexity.

### Maekawa Voting Algorithm

**How It Works**

- Each node is associated with a voting set (a subset of nodes) rather than requiring permission from all nodes.
- A node requests votes from its voting set to enter the critical section. It needs a majority or all votes from its set to proceed.
- Voting sets are designed such that any two sets intersect, ensuring mutual exclusion.

**Pros**

- **Lower message complexity**: Requires fewer messages than Ricart-Agrawala (O(√N) in optimal cases).
- **Decentralized**: No central coordinator, improving fault tolerance.
- **Scalable**: More efficient than requiring all nodes’ permissions.

**Cons**

- **Complex setup**: Designing voting sets to ensure intersection is non-trivial.
- **Deadlock risk**: Improper voting set design or message delays can lead to deadlocks.
- **Limited fault tolerance**: Failure of nodes in a voting set can block progress.

## 8.3. Leader Election Algorithms

### Chang-Roberts Algorithm

**How It Works**

- A leader election algorithm for a ring-based topology.
- Each node sends its unique identifier in a message around the ring.
- When a node receives a message, it compares the received identifier with its own:
  - If the received ID is higher, it forwards the message.
  - If its own ID is higher, it sends its own ID instead.
  - If it receives its own ID, it declares itself the leader and informs others.

**Pros**

- **Simple**: Easy to implement in a ring topology.
- **Low message complexity**: In the best case, O(N) messages; in the worst case, O(N²).
- **Deterministic**: Always elects the node with the highest ID.

**Cons**

- **Ring dependency**: Requires a logical ring, which can break if a node fails.
- **Latency**: Message passing around the ring can be slow in large systems.
- **Assumes unique IDs**: Requires nodes to have distinct identifiers.

### Bully Algorithm

**How It Works**

- A leader election algorithm where nodes have unique identifiers.
- When a node detects the leader has failed (or initiates an election), it sends an election message to all nodes with higher IDs.
- If no higher-ID node responds, it declares itself the leader and notifies others.
- If a higher-ID node responds, it takes over the election process.
- The node with the highest ID eventually becomes the leader.

**Pros**

- **Simple**: Straightforward to implement.
- **Robust**: Works in any topology, not limited to rings.
- **Deterministic**: Always elects the node with the highest ID.

**Cons**

- **High message complexity**: O(N²) in the worst case, as nodes may send messages to all higher-ID nodes.
- **Network overhead**: Frequent elections in unstable systems can flood the network.
- **High-ID node bias**: Always favors the node with the highest ID, which may not be optimal for load balancing.

## Summary Table

| Algorithm       | Type             | Pros                         | Cons                                | Message Complexity |
| --------------- | ---------------- | ---------------------------- | ----------------------------------- | ------------------ |
| Central         | Mutual Exclusion | Simple, low message overhead | Single point of failure, bottleneck | O(1) per request   |
| Ring-Based      | Mutual Exclusion | Simple, fair, no coordinator | High latency, fault intolerant      | O(N) per request   |
| Ricart-Agrawala | Mutual Exclusion | Decentralized, fair          | High message overhead, latency      | O(N) per request   |
| Maekawa Voting  | Mutual Exclusion | Lower message complexity     | Complex setup, deadlock risk        | O(√N) per request  |
| Chang-Roberts   | Leader Election  | Simple, deterministic        | Ring dependency, latency            | O(N) to O(N²)      |
| Bully           | Leader Election  | Simple, robust topology      | High message complexity, bias       | O(N²) worst case   |
