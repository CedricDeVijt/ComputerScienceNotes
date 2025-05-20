## 7.1 Purpose of Replication

### Performance Enhancement

- **Load balancing & latency reduction**: Distribute traffic across servers (e.g., Akamai's 250k global servers).
- **Geographical spreading**: Minimize latency for users accessing data from distant locations (e.g., BBC/YouTube content delivery).

### Increased Availability

- **Fault tolerance**: Probability of system availability = $1 - p^n$, where $p$ = server failure probability.
  - Example: With $p=0.10$, 3 replicas yield 99.9% availability.

### Data Corruption Protection

- **Voting systems**: Requires $2f + 1$ replicas to tolerate $f$ corrupt replicas.
- Example: Financial systems use majority consensus for transaction validation.

## 7.2 Challenges in Replication

### Consistency vs. Availability Trade-offs

- **CAP Theorem**: Distributed systems can only guarantee two of three properties:
  1. **Consistency**: All nodes see the same data
  2. **Availability**: Every request receives a response
  3. **Partition Tolerance**: System operates despite network failures
  - Example: Google App Engine prioritizes availability over strong consistency.

### Bandwidth Overhead

- Replicas require constant synchronization, increasing network traffic.
- Example: Facebook's transition from eventual consistency (Cassandra) to stronger consistency (HBase).

## 7.3 Data-Centric Consistency Models

### Strict Consistency

- **Global clock ordering**: Reads always return the **last written value**.
  - Example: Bank transfers within a single institution.

### Sequential Consistency

- **Fixed operation order**: All processes observe the same interleaved sequence.
  - Example: Multi-bank transactions with causal dependencies.

### Causal Consistency

- **Causal relatedness**: Writes dependent on prior reads must propagate in order.
  - Concurrent writes can be reordered.

### PRAM/FIFO Consistency

- **Per-process write order**: Writes from one process are seen in FIFO order; writes from others can be arbitrary.
  - Example: Social media post visibility delays.

### Weak & Release Consistency

- **Synchronization variables**: Group operations to reduce overhead.
  - Weak: Propagate updates only during synchronization.
  - Release: Separate `acquire` (fetch state) and `release` (propagate updates).

## 7.4 Client-Centric Consistency Models

### Monotonic Reads

- **Guarantee**: Subsequent reads return same or newer data.
  - Example: DNS updates propagate globally; old records never reappear.

### Monotonic Writes

- **Guarantee**: Writes by a client are applied in program order.
  - Example: Version control systems (e.g., Git commits).

### Read-Your-Writes

- **Guarantee**: A client always sees their own updates.
  - Example: Password changes immediately visible to the user.

### Writes-Follow-Reads

- **Guarantee**: Writes occur on the latest read version.
  - Example: Forum comments build on the most recent visible post.

## 7.5 Trade-offs in Consistency Models

### Redundancy vs. Consistency

- Strong consistency requires full replication; weaker models allow partial state.

### Performance Impact

- Strict consistency increases latency (e.g., global locks in financial systems).

### Scalability Limitations

- Strong models (e.g., strict consistency) hinder horizontal scaling.

## Key Points to Remember

- **CAP Theorem→Practical Trade-offs**: Prioritize availability or consistency based on use case ★★★★★
- **Strict vs. Sequential Consistency**: Strict uses global clocks; sequential allows delayed but ordered updates ★★★★☆
- **Client-Centric Models→User Experience**: Focus on client perception rather than system-wide guarantees ★★★★☆
- **Voting Systems→Fault Tolerance**: $2f + 1$ replicas needed to mask $f$ failures ★★★★☆
- **Weak Consistency→Bandwidth Efficiency**: Reduces sync overhead at the cost of temporary inconsistencies ★★★☆☆
- **Eventual Consistency→Scalability**: Used in systems like DNS and early Facebook ★★★☆☆
