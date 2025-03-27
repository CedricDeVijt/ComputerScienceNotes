## 5.1 Evolution from Monolithic to Microservices Architecture

### Monolithic Architecture Challenges

**Monolithic applications** bundle all components (UI, business logic, data access) into a single codebase. Key issues include **spaghetti code**, **limited scalability**, and **technology lock-in**. For example, adding new features often requires redeploying the entire application.

#### Scaling Limitations

- **Vertical scaling** (adding CPU/memory) has physical limits.
- **Horizontal scaling** (replicating monoliths) wastes resources and complicates load balancing.

![[Bachelor 3/Distributed systems/images/Untitled.png]]

### Transitioning to Microservices

**Microservices** decompose applications into **independent, business-capability-aligned services**. Each service:

- Runs in its own process.
- Uses lightweight protocols (e.g., REST, message queues).
- Employs **polyglot persistence** (different databases per service).

![[Bachelor 3/Distributed systems/images/Picture1.webp|5000]]

#### Key Design Shifts

- **Loose coupling**: Services communicate via APIs, not shared libraries.
- **Decentralized governance**: Teams choose their own tech stacks (e.g., Java for billing, Python for recommendations).

## 5.2 Scaling Strategies for Distributed Systems

### Vertical vs. Horizontal Scaling

- **Vertical**: Limited by hardware; suitable for monolithic apps.
- **Horizontal**: Achieved via **service replication** and **load balancers** in microservices.

### Functional Decomposition

Split by business capabilities (e.g., "User Authentication," "Product Catalog"). Example from slide 13:

```
User → Account | Content | Product | Price | Config
```

This reduces interdependencies and enables targeted scaling.

## 5.3 Service-Oriented Architecture (SOA) vs. Microservices

### SOA Characteristics

- **Enterprise Service Bus (ESB)**: Centralized message routing/choreography.
- **Large, reusable services** risk becoming **"monolithic entities"** (slide 18).

### Microservices Differentiation

- **Decentralized communication**: REST over ESB.
- **Fine-grained services**: Smaller than SOA services, organized around specific tasks (e.g., "Shopping Cart" vs. "Order Management").

## 5.4 Containerization as a Microservice Enabler

### Linux Containers (LXC) Fundamentals

- **cgroups**: Control resource allocation (CPU, memory) per container.
- **Namespaces**: Isolate processes, networks, and filesystems.
- **Security**: Linux Security Modules (LSM) restrict capabilities (e.g., `CAP_NET_ADMIN`).

#### Key Container Benefits

- **Lightweight**: Shares host OS kernel; starts in milliseconds.
- **Portability**: Consistent runtime environment from dev to prod.

### Container Management Systems

- **Kubernetes**: Orchestrates scaling, deployment, and service discovery.
- **Docker Swarm**: Native clustering for Docker containers.

## 5.5 Microservice Design Principles

### Smart Services, Dumb Pipes

- **Microservices** handle business logic; communication is simple (REST/Message Queues).
- Avoid complex routing (e.g., ESB) to prevent bottlenecks.

### Decentralized Data Management

- Each service owns its database (e.g., User Service → PostgreSQL, Product Service → MongoDB).
- **Eventual consistency** replaces ACID transactions for resilience.

### DevOps Integration

- **"You build it, you run it"** (Amazon): Teams manage their service’s full lifecycle.
- **CI/CD pipelines** automate testing and deployment (slide 39).

## 5.6 Resilience and Reactive Systems

### The Reactive Manifesto

- **Responsive**: Sub-second latency (e.g., lazy loading in UIs).
- **Elastic**: Auto-scale based on demand (slide 45).
- **Resilient**: Fail gracefully (e.g., Netflix reverting to popular movies if recommendations fail).

### Netflix’s Simian Army

- **Chaos Monkey**: Randomly terminates instances to test fault tolerance.
- **Latency Monkey**: Introduces delays to simulate network issues.

## 5.7 Microservice Frameworks and Tools

### JVM-Based Frameworks

- **Spring Boot**: Simplifies dependency injection and REST API creation.
- **Lagom**: Focuses on event-driven microservices.

### Container Platforms

- **AWS ECS**: Managed Docker orchestration.
- **Azure Container Service**: Kubernetes integration for Azure.

---

## Key Points to Remember

- **Monolith→Microservices Transition** ★★★★☆
  - Decompose by business capabilities; avoid shared databases.
- **Containers→Microservices Synergy** ★★★★★
  - Use cgroups/namespaces for isolation; Kubernetes for orchestration.
- **Resilience→Reactive Design** ★★★★☆
  - Implement circuit breakers and auto-scaling (↗ See Section 6.1).
- **Decentralization→Team Autonomy** ★★★☆☆
  - Allow polyglot tech stacks but enforce API contracts.
- **Pitfall→Over-Splitting Services** ★★★☆☆
  - Too many services increase operational complexity.
