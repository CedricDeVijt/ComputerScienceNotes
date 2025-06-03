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

Consistency models define how updates to shared data are observed by different processes or threads in a distributed or concurrent system. They balance performance and correctness, determining when and how changes made by one process become visible to others. Below, I explain each of the listed consistency models, how they work, and their implications, ordered from strongest to weakest consistency guarantees.

### Strict Consistency

- **Definition**: The strongest consistency model. Any read operation on a data item returns the value of the most recent write operation, regardless of which process or node performs the operation, with no perceptible delay.
- **How it Works**:
  - All operations (reads and writes) appear instantaneous and globally synchronized, as if there’s a single, universal clock.
  - Every node sees the same sequence of operations in real-time, ensuring absolute agreement on data state.
  - Requires perfect synchronization across all processes or nodes, often using a global lock or atomic clock.
- **Example**: A bank account balance updated by a withdrawal must immediately reflect the new balance for all subsequent reads, everywhere.
- **Use Case**: Critical systems like financial transactions or real-time control systems where absolute correctness is non-negotiable.
- **Trade-offs**: High latency and low scalability due to the need for global synchronization. Rarely practical in distributed systems.

### Sequential Consistency

- **Definition**: All processes see all operations (reads and writes) in the same order, but this order may not reflect real-time (wall-clock) order. Each process’s operations appear in program order.
- **How it Works**:
  - Operations are serialized into a single, global sequence that all processes observe.
  - A process’s own operations (e.g., write followed by read) appear in the order they were issued (program order).
  - Different processes may see writes from other processes in different real-time orders, as long as the global sequence is consistent.
  - No requirement for operations to be instantaneous; delays are allowed as long as the order is preserved.
- **Example**: If Process A writes X=1 then Y=2, and Process B reads Y=2 then X=1, the system ensures all processes see writes in the same order (e.g., X=1, Y=2), even if B’s read of Y happens before A’s write to X in real time.
- **Use Case**: Multiprocessor systems or databases where operations must appear atomic and ordered, like in parallel computing.
- **Trade-offs**: Stronger than weaker models but still requires coordination, reducing performance compared to weaker models.

### Causal Consistency

- **Definition**: Operations that are causally related (one operation potentially affects another) must be seen in the correct order by all processes. Unrelated operations may be observed in different orders.
- **How it Works**:
  - Tracks causality using mechanisms like vector clocks or happens-before relationships.
  - If a write W1 causes a write W2 (e.g., W1 triggers W2), all processes see W1 before W2.
  - Concurrent operations (not causally related) can be reordered differently across processes.
  - Reads may return older values if no causal dependency exists.
- **Example**: In a social media platform, if a user posts (W1) and another comments on it (W2), all nodes must see the post before the comment. But two unrelated posts can appear in different orders.
- **Use Case**: Distributed databases, social media feeds, or collaborative applications where causal relationships (e.g., post-comment) matter.
- **Trade-offs**: More relaxed than sequential consistency, allowing better performance but requiring tracking of causal dependencies.

### PRAM / FIFO Consistency

- **Definition**: Pipelined Random Access Memory (PRAM) or FIFO consistency ensures that writes from a single process are seen in the order they were issued (FIFO), but writes from different processes can be observed in any order.
- **How it Works**:
  - Each process’s writes are serialized in the order they were performed (program order).
  - Different processes may see writes from other processes in different orders, as there’s no global synchronization.
  - Reads by a process may not reflect the latest writes from other processes unless explicitly synchronized.
- **Example**: Process A writes X=1 then Y=2. All processes see X=1 before Y=2, but Process B’s writes (e.g., Z=3) may appear before or after A’s writes in different orders across nodes.
- **Use Case**: Systems where individual process order matters but global coordination isn’t needed, like some caching systems.
- **Trade-offs**: Simpler to implement than sequential or causal consistency, offering better performance but weaker guarantees for cross-process interactions.

### Weak Consistency

- **Definition**: No guarantees about the order or visibility of operations unless explicit synchronization points (e.g., locks or barriers) are used.
- **How it Works**:
  - Reads may return stale or inconsistent values unless a synchronization operation (e.g., acquire/release a lock) forces consistency.
  - Writes from different processes can be seen in any order, and there’s no requirement for immediate visibility.
  - Synchronization points ensure all prior writes are visible to all processes.
- **Example**: In a distributed cache, a read might return an old value unless a synchronization operation (like a cache flush) is performed.
- **Use Case**: Systems prioritizing performance, like distributed caches or non-critical data stores, where occasional inconsistency is tolerable.
- **Trade-offs**: High performance and scalability due to minimal coordination, but applications must handle inconsistencies explicitly.

### Release Consistency

- **Definition**: A refinement of weak consistency where writes are guaranteed to be visible only after a process releases a synchronization lock, and reads are consistent only after acquiring a lock.
- **How it Works**:
  - Divides synchronization into **acquire** (start of critical section) and **release** (end of critical section).
  - Writes performed in a critical section are propagated to other processes only upon release.
  - Reads in a critical section see the latest writes from prior releases.
  - Outside critical sections, no consistency guarantees apply.
- **Example**: In a database, a process updates multiple records in a transaction (critical section). Other processes see all updates only after the transaction commits (release).
- **Use Case**: Distributed shared memory systems or databases with transactional updates.
- **Trade-offs**: Better performance than sequential consistency by limiting consistency enforcement to synchronization points, but requires careful use of locks.

### Entry Consistency

- **Definition**: A further refinement of release consistency where consistency is enforced only for specific data items associated with a synchronization object (e.g., a lock).
- **How it Works**:
  - Each data item is tied to a specific synchronization variable (e.g., a lock).
  - When a process acquires a lock for a data item, it sees all previous writes to that item made by processes that released the same lock.
  - Writes to unrelated data items or without synchronization are not guaranteed to be visible.
  - Requires explicit association between data and synchronization variables.
- **Example**: In a distributed system, a process locks a specific record (e.g., a user profile) and sees all prior updates to that record upon acquiring the lock, but not updates to other records.
- **Use Case**: Fine-grained control in distributed shared memory or object-oriented databases where specific data items need consistency.
- **Trade-offs**: High performance due to localized consistency, but complex to implement due to the need to associate data with synchronization objects.

### Summary and Comparison

| **Model**  | **Guarantees**                               | **Performance** | **Use Case**                          | **Complexity** |
| ---------- | -------------------------------------------- | --------------- | ------------------------------------- | -------------- |
| Strict     | Real-time, global order                      | Very low        | Financial systems, critical control   | Very high      |
| Sequential | Global operation order, program order        | Low             | Multiprocessors, databases            | High           |
| Causal     | Causal order, unrelated ops may vary         | Moderate        | Social media, collaborative apps      | Moderate       |
| PRAM/FIFO  | Per-process order, no global order           | Moderate-high   | Caching, simple distributed systems   | Moderate       |
| Weak       | No order without sync                        | High            | Distributed caches, non-critical data | Low            |
| Release    | Consistency at sync points (release/acquire) | High            | Transactions, shared memory           | Moderate       |
| Entry      | Consistency for specific data at sync points | Very high       | Fine-grained distributed systems      | High           |

### Key Insights

- **Stronger models** (strict, sequential) ensure predictable behavior but sacrifice performance due to synchronization overhead.
- **Weaker models** (weak, release, entry) optimize for performance and scalability but require applications to manage inconsistencies or use explicit synchronization.
- **Causal and PRAM** strike a balance, suitable for systems where partial ordering is sufficient.
- **Choosing a model** depends on the application’s needs: critical systems need stronger models, while high-performance systems tolerate weaker ones.

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

Replication involves balancing the CAP theorem (Consistency, Availability, Partition Tolerance).

- **C**: Consistency ensures all replicas reflect the same data.
- **A**: Availability guarantees that requests receive a response.
- **P**: Partition Tolerance allows the system to function despite network failures.

No system can guarantee all three simultaneously:

- **CP systems**: prioritize consistency and partition-tolerance, sacrificing availability.
- **AP systems**: prioritize availability and partition-tolerance, sacrificing strict consistency.
- **CA systems**: technically only work if partitions are not considered — not realistic for distributed systems.

### Examples

- **Google Spanner**: Uses synchronous replication with strong consistency across global data centers.
- **Apache Cassandra**: Employs asynchronous replication with tunable consistency for high availability.
- **Redis Cluster**: Supports master-slave replication for fast, in-memory data access.

Replication is a cornerstone of distributed systems, enabling resilience and performance but requiring careful design to manage trade-offs effectively.
