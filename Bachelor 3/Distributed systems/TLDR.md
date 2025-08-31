## 1 Introduction

### Definitions

**Service**: part of a computer system managing a collection of related resources, presenting their functionality to users and applications
**server**: a running program (a process) that accepts requests from programs running on other computers (clients) to perform a service, and responds appropriately
**client**: running process on networked computer sending service requests to server
**remote invocation**: complete interaction between client and server to process single request

### Motivation

- Cost: cheaper to use many low-cost systems than one high-end system
- Capability: some problems too large for single system (memory, data storage, computational requirements)
- Concurrency: many problems have inherent options for parallelism
- Reliability: distributing redundant components minimizes probability faults impact user
- Integration: for organizations to interact, their systems need to interact
- Distribution: many applications inherently distributed as users are geographically spread (e.g. email, WWW)

### Challenges

- Heterogeneity: different hardware, OS, programming languages, network technologies
- Openness: systems need to be extensible and support new services, protocols, etc.
- Security: need to protect data and resources from unauthorized access and attacks
- Scalability: system must work efficiently as it grows in size and complexity
- Fault tolerance: system must continue to operate despite failures of components
- Transparency: hide complexity of distributed system from users and applications

### Distributed system architectures

#### Logical architecture styles

##### Coupled architectures

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

##### Decoupled architectures

- loosely coupled systems with low degree of interdependence
- Adding/removing a component is easy

**Event-based architecture**

- components communicate by producing and consuming events

Pros:

- loose coupling of components
- high scalability

Cons:

- complex event management

** Data-centric architecture**

- components share a common data store

Pros:

- simplified data sharing
- easier data management

Cons:

- potential bottleneck at data store
- complex data consistency management

### Client server architectures

- clients request services from servers
- servers provide services to clients

**"simple" client-server architecture**: clients directly communicate with servers
**client-multiserver architecture** (explicit server lookup): clients communicate with multiple servers, often via a directory service
**client-multiserver architecture** (implicit server lookup): clients communicate with multiple servers, often via a load balancer
**proxy architecture**: clients communicate with servers via a proxy that forwards requests and responses

### Peer-to-peer architectures

- all nodes are equal and can act as both clients and servers
- nodes communicate directly with each other

## 2 Middleware and Communication

### Achieve basic communication

- Berkeley socket
- Socket pair described by 4 -tuple (source IP, source port, dest IP, dest port)

### Why middleware?

- Role of middleware: Hide complexity of network communication, provide standard communication patterns, enable focus on application logic rather than infrastructure BUT programmer should know object is remote

- Remote object references: local object that represents a remote object, allowing clients to invoke methods on remote objects as if they were local

- local/remote method invocations: local method invocations are direct calls to methods on local objects, while remote method invocations involve communication over a network to invoke methods on remote objects

#### Fault tolerances

1. **Retry**: automatically retry failed operations a certain number of times before giving up
2. **Duplicate filtering**: detect and discard duplicate messages to prevent processing the same request multiple times
3. **Retransmission**: resend lost or corrupted messages to ensure reliable communication
   3.1 Re-execution: re-execute operations that may have failed due to transient errors
   3.2 Retransmit old reply: resend previous responses to clients if the original response was lost

#### Invocation semantics

What guarantees are given on the number of executions of remote method invocations?

| Semantic          | Retransmit request<br><br>message | Duplicate<br><br>filtering | Re-execute procedure<br><br>or retransmit reply |
| ----------------- | --------------------------------- | -------------------------- | ----------------------------------------------- |
| **Maybe**         | No                                | Not applicable             | Not applicable                                  |
| **At-least-once** | Yes                               | No                         | Re-execute procedure                            |
| **At-most-once**  | Yes                               | Yes                        | Retransmit old reply                            |

### Middleware architecture

#### Proxy

- Client-side component that represents the remote object
- Marshals method calls into network messages
- Sends request messages to the server

#### Skeleton

- Server-side component that receives network messages, acts like the local invoker to the object
- Unmarshals messages into method calls on the actual remote object
- Sends reply messages back to the client

#### Marshalling/Unmarshalling

- Process of converting objects to/from byte streams for network transmission
- Standards: Java Serialization, Protocol Buffers (Google), CORBA CDR

#### Communication modules

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

### 3 Service-Oriented Architectures

**Service**: self-contained unit of functionality that exposes its capabilities through a well-defined interface, can be independently deployed and managed, and is designed to be reusable and composable with other services.

**Service-oriented architecture (SOA)**: architectural style that structures applications as a collection of loosely coupled services that communicate over a network, often defined in terms of contracts, focuses on shared, reusable and loosely coupled services.

**Architecture**: set of principles and guidelines for designing and building software systems, including components, their interactions, and the overall structure of the system.

#### Multi-tenancy

- single instance of software serves multiple customers (tenants)
- each tenant's data is isolated and remains invisible to other tenants

- **Data multitenancy**: multiple tenants share the same database schema, with tenant-specific data identified by a tenant ID
- **Application multitenancy**: each tenant has its own instance of the application, allowing for greater customization and isolation

#### Cloud computing

Cloud computing is a model for enabling convenient, on-demand network access to a shared pool of configurable computing resources

#### X as a Service (XaaS)

- **Infrastructure as a Service (IaaS)**: provides virtualized computing resources over the internet, such as virtual machines, storage, and networking
- **Platform as a Service (PaaS)**: provides a platform allowing customers to develop, run, and manage applications without dealing with the underlying infrastructure
- **Software as a Service (SaaS)**: provides access to software applications over the internet, typically through a web browser, eliminating the need for local installation and maintenance

Examples:

- IaaS: Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP)
- PaaS: Heroku, Google App Engine, Microsoft Azure App Service
- SaaS: Google Workspace (Gmail, Docs), Microsoft 365, Salesforce

#### Payment models

1. **Per-instance**: pay for each instance of a service used
2. **Reserved**: pay upfront for a reserved capacity of a service
3. **Bidding**: bid for unused capacity of a service at a lower price
4. **Metered**: pay based on actual usage of a service (e.g., compute hours, storage used)

### 4 Web Services

**Web service**: software system designed to support interoperable machine-to-machine interaction over a network, typically using standard protocols such as HTTP and data formats like XML or JSON.

#### Web services in theory and practice

**Web service**: software system designed to support interoperable machine-to-machine interaction over a network, typically using standard protocols such as HTTP and data formats like XML or JSON.

**Web services** are used in various applications, including:

- Enterprise applications: integrating different systems within an organization
- E-commerce: enabling online transactions and interactions between buyers and sellers
- Social media: allowing third-party applications to interact with social media platforms
- Mobile applications: providing backend services for mobile apps
- Cloud computing: enabling access to cloud-based services and resources

#### RESTful Web Services

#### SOAP Web Services

**SOAP (Simple Object Access Protocol)**: protocol for exchanging structured information in web services, using XML as the message format and typically relying on HTTP or SMTP for message transmission.

#### Web Service VS Service Oriented Architecture

| Feature                | Web Service                                                       | Service-Oriented Architecture (SOA)                                                      |
| ---------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Definition             | Software system for machine-to-machine interaction over a network | Architectural style structuring applications as a collection of loosely coupled services |
| Communication Protocol | Typically uses HTTP, XML, JSON                                    | Can use various protocols (HTTP, JMS, etc.)                                              |
| Service Granularity    | Can be fine-grained or coarse-grained                             | Typically coarse-grained services                                                        |
| Interoperability       | High, due to standard protocols and formats                       | High, but depends on service design and implementation                                   |
| Reusability            | Services can be reused across different applications              | Emphasizes reuse of services across the enterprise                                       |
| Loose Coupling         | Yes, services are designed to be independent                      | Yes, services are loosely coupled                                                        |

#### REST vs SOAP

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

#### When to use which?

- Use REST for simple, lightweight, and scalable web services that require flexibility and performance.
- Use SOAP for complex, enterprise-level web services that require strict standards, built-in security, and transactional reliability.

### 5 Microservices
