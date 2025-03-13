## 3.1 Foundations of Distributed Systems

### Basic Architecture Components

**Nodes** consist of processes, middleware, and local OS communicating via **message passing** only. Distributed applications scale to hundreds of thousands of servers.
**Key Challenge**: Organizing processes efficiently in large-scale systems.

### Scalability Limitations in Early Systems

#### Case Study: Twitter's Monolithic Architecture (2006-2010)

- Used **Monorail** framework with **MySQL** storage
- Layers: Presentation (HTTP/Thrift), Logic (Thrift\*), Storage (MySQL)
- **Weaknesses**:
  - Storage I/O bottlenecks
  - Tight coupling between components
  - Synchronization issues ("too many cooks in the kitchen")

## 3.2 Service-Oriented Architectures (SOA): Principles & Evolution

### Core Design Philosophy

- **Services** are **loosely coupled**, reusable components communicating via standardized interfaces
- Contrast with **tightly coupled systems** (e.g., monolithic apps):
  - Tight: Component changes require system-wide updates
  - Loose: Independent service modification (↗ See Twitter case study)

### Historical Implementations

#### CORBA vs. Web Services

- **CORBA**: Language/OS-agnostic but complex; limited vendor support
- **Web Services**: Modern standard using HTTP/SOAP/REST; supports mixed environments

### Multi-Tenancy in SOA

**Definition**: Single service instance serving multiple tenants (client organizations).
**Levels**:

1. Shared hardware (IaaS)
2. Shared OS/database (PaaS)
3. Shared application kernel (SaaS)

## 3.3 Cloud Computing Fundamentals

### NIST Definition

Cloud computing enables **on-demand access** to shared, configurable resources (e.g., networks, servers) with **rapid elasticity** and pay-per-use pricing.

### Service Models Hierarchy

#### IaaS (Infrastructure as a Service)

- Unit: **Virtual Machine** (e.g., AWS EC2)
- Provider manages hypervisor/physical hardware

#### PaaS (Platform as a Service)

- Constrained dev environment (e.g., Heroku)
- Trade-off: Efficiency vs. vendor lock-in

#### SaaS (Software as a Service)

- Provider-managed apps (e.g., Gmail, Salesforce)
- **Mnemonic**: "I Prefer Skipping Apples" = IaaS → PaaS → SaaS (bottom to top)

## 3.4 Deployment & Economic Models

### Deployment Types

- **Public Cloud**: Shared resources over internet (e.g., AWS)
- **Private Cloud**: Dedicated infrastructure for secure data
- Hybrid/Community: Mixed or collaborative setups

### Payment Strategies

1. **Per-instance billing**: Pay hourly for active VMs (risk: idle costs)
2. **Reserved usage**: Lower rates via upfront commitment
3. **Spot bidding**: Bid for unused capacity (cost varies with demand)

---

## Key Points to Remember

- **Tight vs. Loose Coupling** ★★★★☆
  - Tight: Component changes disrupt system (e.g., Twitter's early MySQL setup)
  - Loose: Independent services (SOA/cloud) enable scalability
- **Multi-Tenancy Levels** ★★★☆☆
  - IaaS→PaaS→SaaS = Increasing abstraction/provider control
- **Cloud Payment Models** ★★★☆☆
  - Spot bidding optimizes costs but requires load forecasting
- **SOA ≠ Product** ★★☆☆☆
  - Implementation varies (CORBA, Web Services, EJB)
- **NIST Cloud Criteria** ★★★★★
  - On-demand access, resource pooling, rapid elasticity, measured service
- **Mnemonic**: "SOA solves TIGHT issues"
  - **T**hrottled scalability → **I**O bottlenecks → **G**overnance conflicts → **H**igh coupling → **T**eam silos
