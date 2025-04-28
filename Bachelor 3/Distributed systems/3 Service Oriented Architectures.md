## 3.1 Distributed Systems Fundamentals

### Core Components and Communication

A distributed system consists of **networked hardware/software components** that coordinate actions **exclusively through message passing**. Each node contains processes, middleware, and a local OS.
**Key Question**: How do scaling challenges emerge when moving from single-node to multi-node architectures?

#### Node Structure

- **Node A/B Architecture**:
  Process → Middleware → Local OS
  Communication via network layer

#### Scaling Challenges

Modern applications (e.g., Twitter) may involve **hundreds of thousands of servers**. Organizing processes efficiently becomes critical to avoid bottlenecks.

## 3.2 Evolution to Service-Oriented Architectures (SOA)

### Defining SOA Principles

SOA is a **design style** where capabilities are exposed as reusable, loosely coupled **services** with standardized interfaces.
**Key Question**: How does SOA differ from monolithic application design?

#### Core Characteristics

- **Loose Coupling**: Services interact via contracts, not direct dependencies.
- **Reusability & Exchangeability**: Services can be reused across applications or replaced without system-wide impact.
- **Multi-Tenancy**: Single service instance serves multiple clients.

#### Technical Realizations

- **Historical Approaches**: CORBA (complex, language-agnostic), Enterprise Java Beans (Java-only).
- **Modern Standards**: Web Services (flexible, mixed protocols).

## 3.3 Case Study: Twitter’s Transition to SOA

### Initial Architecture and Challenges

- **Monolithic Design**:
  Presentation (HTTP/THRIFT) → Logic → Storage (MySQL).
- **Pain Points**:
  Storage I/O bottlenecks, poor concurrency, tight coupling, unclear ownership.

#### Transition to SOA

- **Service Decomposition**:
  Tweet Service, User Service, Timeline Service, etc.
- **Decoupled Storage**:
  Memcached/Redis for caching, MySQL for persistence.

**Critical Distinction**: Moving from a "stovepipe system" (data silos, redundancy) to modular services resolved synchronization issues.

## 3.4 Tightly vs. Loosely Coupled Architectures

### Tightly Coupled Systems

- **Characteristics**: Direct dependencies (e.g., method calls between objects).
- **Drawbacks**: Difficult to modify; failure in one component cascades.
- **Example**: Traditional telecom Operating Support Systems with rigid data flows.

### Loosely Coupled Systems

- **Characteristics**: Interaction via event buses or shared data spaces.
- **Advantages**: Easier scalability, fault isolation.
- **Example**: SOA’s service bus model (↗ See Section 2.1.1).

## 3.5 Cloud Computing Models and Deployment

### Service Models (XaaS)

- **IaaS**: Virtualized infrastructure (e.g., AWS EC2).
- **PaaS**: Development environments with built-in scaling (e.g., Heroku).
- **SaaS**: Provider-managed applications (e.g., Salesforce).

**Hierarchy**: SaaS → PaaS → IaaS (increasing provider control).

### Deployment Models

- **Public Cloud**: Shared resources (e.g., AWS, Azure).
- **Private Cloud**: Dedicated infrastructure for secure data.
- **Hybrid/Community**: Mixed or shared organizational setups.

#### Payment Models

- Per-instance billing, reserved usage, bidding, actual usage.

## 3.6 Multi-Tenancy in SOA and Cloud

### Types of Multi-Tenancy

- **Data-Level**: Same application, tenant-specific data conditions.
- **Application-Level**: Tenant-customized configurations on a core kernel.

**Key Question**: How does multi-tenancy reduce operational costs in cloud environments?

#### Implementation Challenges

- Security isolation, performance tuning, avoiding vendor lock-in.

## 3.7 Historical Context and Modern Implementations

### Distributed Computing Evolution

- **1.0 Era**: Tightly coupled systems (e.g., telecom networks).
- **2.0 Era**: SOA and cloud-native designs (e.g., Facebook’s microservices).

#### Legacy Technologies

- **CORBA**: Early attempt at language-agnostic services.
- **Web Services**: Current standard enabling interoperability.

---

## Key Points to Remember

- **SOA vs. Monolithic → Loose Coupling**: ★★★★☆
  Enables modular updates and scalability.
- **Cloud Service Models → Hierarchy**: ★★★☆☆
  SaaS builds on PaaS/IaaS; trade-offs between control and convenience.
- **Multi-Tenancy → Cost Efficiency**: ★★★★☆
  Critical for scalable cloud economics but requires robust isolation.
- **Tight Coupling → Risk of Cascading Failures**: ★★★★☆
  Common in legacy systems; mitigated by SOA.
- **Twitter Case Study → Storage Decoupling**: ★★★★★
  Resolved I/O bottlenecks via Redis/MySQL separation.
- **Payment Models → Flexibility**: ★★★☆☆
  Bidding/usage-based models optimize costs for dynamic workloads.
