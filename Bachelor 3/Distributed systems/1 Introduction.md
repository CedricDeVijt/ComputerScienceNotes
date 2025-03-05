## 1.1 Introduction to Distributed Systems

### Definition

- A distributed system is a collection of independent computers appearing as a **single coherent system** to users.
- **Components**:
  - Nodes (computers/processes) connected via a network.
  - Middleware layer abstracts local OS differences.

### Examples

- **Web Systems**: World Wide Web, DNS, HTTP/HTTPS protocols.
- **Cloud Computing**: Google datacenters, AWS.
- **Peer-to-Peer (P2P)**: BitTorrent (tracker, swarm, seeder, leecher).
- **Service Providers**: YouTube, Amazon, Twitter.

### Key Components

- **Service**: Manages resources and exposes functionality via operations (e.g., streaming, storage).
- **Client-Server Model**:
  - **Server**: Process accepting and responding to requests.
  - **Client**: Process invoking service operations.
- **Remote Invocation**: Complete interaction (request + response) between client and server.

## 1.2 Distributed System Architectures

### Logical Architectures

1. **Coupled**:
   - Tightly linked components (e.g., layered, object-based).
   - Pros: Reduced interfaces, easy layer replacement.
   - Cons: Duplication, complexity.

  ![](/Bachelor%203/Distributed%20systems/images/Pasted%20image%2020250220150049.png)

1. **Decoupled**:
   - Loosely linked components (e.g., event-based, data-centric).
   - Pros: Flexibility, integration of legacy systems.
   - Cons: Bottlenecks, locking issues.

  ![](/Bachelor%203/Distributed%20systems/images/Pasted%20image%2020250220150106.png)

### System Architectures

- **Client-Server**:
  - Simple (direct request-reply) or multi-server (load balancing via DNS/proxy).
- **Peer-to-Peer (P2P)**:
  - Decentralized, self-organizing nodes acting as both clients and servers (servants).
  - Features: GUIDs, volatile nodes, structured/unstructured overlays.

## 1.3 Motivations and Challenges

### Why Use Distributed Systems?

- **Cost**: High performance per dollar with commodity hardware.
- **Capability**: Solve large-scale problems (memory, computation, storage).
- **Concurrency**: Parallelism for efficiency.
- **Reliability**: Redundancy minimizes fault impact.
- **Integration**: Cross-organization collaboration.

### Challenges

- No global time or spatial limits.
- Partial failures and concurrency.
- Complexity in management.

---

## Key Points to Remember

- **Definition**: Distributed systems appear as a single system despite multiple independent nodes.
- **Components**: Services, clients, servers, middleware.
- **Architectures**: Coupled (layered/object-based) vs. decoupled (event/data-centric); client-server vs. P2P.
- **Remote Invocation**: Fundamental interaction model (request-response).
- **Motivations**: Cost, capability, concurrency, reliability.
- **Key Technologies**: Docker, Kubernetes, Hadoop, BitTorrent.
- **Challenges**: Partial failures, lack of global time, concurrency management.
