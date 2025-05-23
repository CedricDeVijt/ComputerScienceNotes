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


## More info

Replication in distributed systems is the process of maintaining multiple copies of data or services across different nodes (servers or computers) in a network to improve reliability, availability, performance, and fault tolerance. Here's an overview:

### Key Concepts
1. **Purpose of Replication**:
   - **Availability**: Ensures data or services remain accessible even if some nodes fail.
   - **Fault Tolerance**: Allows the system to continue functioning despite hardware or software failures.
   - **Performance**: Distributes workload across nodes, reducing latency by serving data from geographically closer replicas.
   - **Scalability**: Supports increased demand by balancing requests across multiple replicas.

2. **Types of Replication**:
   - **Full Replication**: Every node stores a complete copy of the data. Common in systems requiring high availability but can be resource-intensive.
   - **Partial Replication**: Only specific subsets of data are replicated on certain nodes, optimizing storage but requiring careful coordination.
   - **Active Replication**: All replicas process requests simultaneously, often used for fault-tolerant systems (e.g., in real-time control systems).
   - **Passive (Primary-Backup) Replication**: One node (primary) handles requests, while others (backups) synchronize with it, taking over if the primary fails.

3. **Replication Models**:
   - **Synchronous Replication**: Updates are applied to all replicas simultaneously, ensuring strong consistency but potentially increasing latency.
   - **Asynchronous Replication**: Updates are propagated to replicas with some delay, improving performance but risking temporary inconsistencies.
   - **Quorum-Based Replication**: A subset of replicas (quorum) must agree on updates, balancing consistency and availability.

4. **Consistency Models**:
   - **Strong Consistency**: All replicas reflect the same data at all times, often requiring synchronous updates.
   - **Eventual Consistency**: Replicas may temporarily diverge but will eventually converge to the same state, common in asynchronous systems.
   - **Causal Consistency**: Ensures operations that are causally related are applied in the correct order across replicas.

5. **Challenges in Replication**:
   - **Consistency vs. Performance**: Strong consistency slows down operations due to coordination overhead, while weaker models risk stale data.
   - **Conflict Resolution**: In multi-master replication, concurrent updates to the same data can cause conflicts, requiring mechanisms like versioning or last-writer-wins.
   - **Network Partitions**: Splits in the network can lead to inconsistent replicas, addressed by protocols like Paxos or Raft.
   - **Resource Overhead**: Replication increases storage, bandwidth, and computational requirements.

6. **Replication Strategies**:
   - **Master-Slave**: One node (master) handles writes, while others (slaves) replicate data for reads.
   - **Multi-Master**: Multiple nodes can handle writes, increasing complexity but improving availability.
   - **Sharding with Replication**: Data is partitioned (sharded) across nodes, with each shard replicated for redundancy.

7. **Use Cases**:
   - **Databases**: Systems like MySQL, MongoDB, or Cassandra use replication for high availability and load balancing.
   - **Content Delivery Networks (CDNs)**: Replicate web content across edge servers to reduce latency.
   - **Distributed File Systems**: Systems like Hadoop HDFS replicate data blocks for fault tolerance.
   - **Cloud Services**: AWS S3 or Google Cloud Spanner replicate data across regions for durability and availability.

### Trade-Offs
Replication involves balancing the CAP theorem (Consistency, Availability, Partition Tolerance). No system can guarantee all three simultaneously:
- **CP Systems**: Prioritize consistency and partition tolerance (e.g., banking systems).
- **AP Systems**: Prioritize availability and partition tolerance (e.g., social media platforms).

### Examples
- **Google Spanner**: Uses synchronous replication with strong consistency across global data centers.
- **Apache Cassandra**: Employs asynchronous replication with tunable consistency for high availability.
- **Redis Cluster**: Supports master-slave replication for fast, in-memory data access.

Replication is a cornerstone of distributed systems, enabling resilience and performance but requiring careful design to manage trade-offs effectively.