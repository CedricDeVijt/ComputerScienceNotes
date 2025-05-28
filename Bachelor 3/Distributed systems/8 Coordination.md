## 8.1 Problem Statement & Requirements

**Critical section coordination** for N processes without shared variables.

- **Safety**: At most one process in CS at any time.
- **Liveness**: No deadlock/starvation; requests eventually granted.
- **Fairness**: Requests ordered by Lamport clocks (logical timestamps).

### Evaluation Metrics

1. **Bandwidth**: Messages per enter/leave operation.
2. **Client Delay**: Time to enter/leave (unloaded system).
3. **Synchronization Delay**: Lost time between CS exits/entries (loaded system).

## 8.2 Central Server Algorithm

**Token-based coordination via central authority**.

- **Client Flow**:
  - `enter()`: Send Request → Wait for Grant (2 messages).
  - `leave()`: Send Leave (1 message).
- **Server Flow**:
  - Grant token if free; else enqueue requests.

### Efficiency Analysis

- **Bandwidth**: 2 messages/enter, 1/leave.
- **Client Delay**: $2\delta$ (RTT for Grant).
- **Sync Delay**: $2\delta$ (server processing).

## 8.3 Ring-Based Algorithm

**Logical ring with circulating token**.

- **Token Passing**: Only token holder enters CS.
- **Safety**: Token possession guarantees exclusivity.
- **Liveness**: Token circulates indefinitely.

### Efficiency Analysis

- **Bandwidth**: Average $(N+1)/2$ messages/enter (token traversal).
- **Client Delay**: Average $N\delta/2$.
- **Sync Delay**: $(N+1)\delta/2$.

## 8.4 Ricart-Agrawala Algorithm

**Multicast-based with Lamport clocks**.

- **Process Flow**:
  1. Multicast Request($T_i, p_i$) to all.
  2. Enter CS after collecting $N-1$ Replies.
  3. Release and Reply to queued Requests.

### Safety Proof

Contradiction: Two processes in CS would require mutual Replies, violating Lamport ordering.

### Efficiency Analysis

- **Bandwidth**: $2N-1$ messages/enter (multicast + replies).
- **Sync Delay**: $\delta$ (single message round).

## 8.5 Maekawa Voting Algorithm

**Voting subsets for reduced coordination**.

- **Voting Set ($V_i$)**: Each process requires $K=\sqrt{N}$ votes.
- **Overlap Requirement**: $V_i \cap V_j \neq \emptyset$ for safety.

### Algorithm Flow

- `enter()`: Request votes from $V_i$.
- `leave()`: Release votes to $V_i$.

### Limitations

- **Deadlock Risk**: Resolved using Lamport clocks.
- **Efficiency**:
  - Bandwidth: $2K$ messages/enter, $K$/leave.
  - Sync Delay: $2\delta$.

## 8.6 Election Mechanisms

### Chang-Roberts Ring Algorithm

**Elect highest-ID process via token circulation**.

- **Process Flow**:
  - Forward Election(ID) if received ID < own ID.
  - Declare self leader if token completes full circle.

#### Safety & Liveness

- **Safety**: Unique IDs prevent multiple leaders.
- **Liveness**: Guaranteed in failure-free, asynchronous systems.

#### Efficiency

- **Bandwidth**: $O(N)$ to $O(N^2)$ messages.
- **Turnaround Time**: $O(N\delta)$.

### Bully Algorithm

**Timeout-based leader election with crash recovery**.

- **Process Flow**:
  1. Send Election to higher-ID processes.
  2. If no Answer, declare self leader.
  3. Broadcast Coordinator to lower IDs.

#### Crash Handling

- Higher-ID processes "bully" lower IDs into submission.

#### Efficiency

- **Worst-Case Bandwidth**: $O(N^2)$ messages.
- **Turnaround Time**: Dependent on timeout $T$.

---

## Key Points to Remember

- **Mutual Exclusion → Central Server Simplicity** ★★★★☆
  - Low message overhead but single-point failure risk.
- **Scalability → Maekawa Voting** ★★★☆☆
  - Reduces messages via subsets but requires deadlock handling.
- **Fairness → Ricart-Agrawala Lamport Clocks** ★★★★★
  - Logical timestamps enforce request order.
- **Election Safety → Unique IDs in Chang-Roberts** ★★★★☆
  - Ensures only one leader via ring traversal.
- **Crash Recovery → Bully Algorithm Timeouts** ★★★☆☆
  - Effective in synchronous systems but message-heavy.
- **Critical Metric → Synchronization Delay** ★★★★★
  - Ricart-Agrawala ($δ$) outperforms Ring ($Nδ/2$).
- **Common Pitfall**: Assuming reliable networks for liveness.

## 8.7 More info

Coordination refers to the mechanisms and protocols that enable multiple independent processes, nodes, or components to work together to achieve a common goal, maintain consistency, and manage shared resources despite being geographically or logically separated. It addresses challenges like synchronization, communication, fault tolerance, and consensus in environments where nodes may fail, messages may be delayed or lost, and no single node has a complete view of the system.

### Why Coordination is Necessary

Distributed systems consist of multiple nodes (computers, servers, or processes) that communicate over a network. Coordination is critical because:

- **No Centralized Control**: Nodes operate independently without a single point of control.
- **Concurrency**: Multiple nodes may access shared resources simultaneously, risking conflicts.
- **Partial Failures**: Nodes or network links may fail, requiring mechanisms to maintain system reliability.
- **Asynchronous Communication**: Message delays and varying processing speeds complicate synchronization.
- **Consistency Requirements**: Applications often need guarantees about data consistency or task ordering across nodes.

Coordination ensures nodes agree on actions, states, or resource usage, enabling the system to function reliably and efficiently.

### Key Problems in Coordination

Coordination in distributed systems tackles several core challenges:

#### Consensus

Consensus involves nodes agreeing on a single value or decision, even in the presence of failures. It’s critical for tasks like:

- **Leader Election**: Choosing a single node to act as a coordinator (e.g., in a distributed database).
- **State Machine Replication**: Ensuring all nodes apply the same sequence of operations (e.g., in fault-tolerant systems).
- **Distributed Transactions**: Agreeing on whether to commit or abort a transaction.

**Example Algorithms**:

- **Paxos**: A robust protocol for achieving consensus in asynchronous systems with crash failures. It’s complex but ensures safety (agreement) and liveness (progress) under certain conditions.
- **Raft**: A more understandable consensus algorithm that breaks down leader election, log replication, and safety into manageable steps. Used in systems like etcd and Consul.
- **Byzantine Fault Tolerance (BFT)**: Handles malicious nodes or arbitrary failures (e.g., PBFT, used in blockchain systems).

#### Synchronization

Synchronization ensures that nodes perform actions in a specific order or at specific times, avoiding race conditions or inconsistent states.

- **Mutual Exclusion**: Ensures only one node accesses a shared resource at a time (e.g., a distributed lock for a shared file).
- **Event Ordering**: Guarantees that operations or messages are processed in a consistent order across nodes.
- **Time Synchronization**: Aligns clocks across nodes to coordinate time-sensitive operations.

**Techniques**:

- **Distributed Locks**: Tools like Zookeeper or Chubby provide distributed locking mechanisms.
- **Logical Clocks**: Lamport clocks or vector clocks assign timestamps to events to establish causality without relying on synchronized physical clocks.
- **Physical Clock Synchronization**: Protocols like NTP (Network Time Protocol) align node clocks, though perfect synchronization is impossible due to network delays.

### Common Distributed Algorithms

#### **Central Algorithm**

##### How It Works

- A single coordinator node manages access to a shared resource (e.g., for mutual exclusion).
- Nodes send requests to the coordinator, which grants access based on a queue or priority system.
- The coordinator ensures only one node accesses the resource at a time.

##### Pros

- **Simple**: Easy to implement and understand.
- **Deterministic**: Centralized control ensures predictable behavior.
- **Low message overhead**: Nodes only communicate with the coordinator.

##### Cons

- **Single point of failure**: If the coordinator fails, the system halts.
- **Scalability issues**: The coordinator can become a bottleneck in large systems.
- **High latency**: All requests must go through the coordinator, increasing delay in large networks.

#### **Ring-Based Algorithm**

##### How It Works

- Nodes are organized in a logical ring topology.
- A token or message circulates around the ring. For mutual exclusion, only the node holding the token can access the shared resource.
- For leader election (e.g., Chang-Roberts variant), nodes pass messages to elect a leader based on identifiers.

##### Pros

- **Simple structure**: Easy to implement in systems with a ring topology.
- **Fairness**: Nodes get equal opportunity to access resources as the token circulates.
- **No central coordinator**: Avoids single point of failure.

##### Cons

- **High latency**: Token must traverse the entire ring, which can be slow in large systems.
- **Fault intolerance**: If a node fails, the ring breaks, disrupting the algorithm unless recovery mechanisms are in place.
- **Inefficient for sparse access**: If only a few nodes need the resource, the token still circulates through all nodes.

#### **Ricart-Agrawala Algorithm**

##### How It Works

- A distributed mutual exclusion algorithm where nodes request access to a critical section by sending timestamped messages to all other nodes.
- A node grants permission to another node only if it is not in or requesting the critical section itself, using logical timestamps to resolve conflicts.
- A node enters the critical section only after receiving permission from all other nodes.

##### Pros

- **Decentralized**: No single point of failure.
- **Fairness**: Timestamps ensure requests are processed in order.
- **Robust**: Works in fully distributed systems without requiring a coordinator.

##### Cons

- **High message complexity**: Requires O(N) messages per request (N = number of nodes), leading to network overhead.
- **Latency**: Waiting for all permissions can be slow, especially in large systems.
- **Clock synchronization**: Relies on logical clocks, which may introduce complexity.

#### **Maekawa Voting Algorithm**

##### How It Works

- Each node is associated with a voting set (a subset of nodes) rather than requiring permission from all nodes.
- A node requests votes from its voting set to enter the critical section. It needs a majority or all votes from its set to proceed.
- Voting sets are designed such that any two sets intersect, ensuring mutual exclusion.

##### Pros

- **Lower message complexity**: Requires fewer messages than Ricart-Agrawala (O(√N) in optimal cases).
- **Decentralized**: No central coordinator, improving fault tolerance.
- **Scalable**: More efficient than requiring all nodes’ permissions.

##### Cons

- **Complex setup**: Designing voting sets to ensure intersection is non-trivial.
- **Deadlock risk**: Improper voting set design or message delays can lead to deadlocks.
- **Limited fault tolerance**: Failure of nodes in a voting set can block progress.

#### **Chang-Roberts Algorithm**

##### How It Works

- A leader election algorithm for a ring-based topology.
- Each node sends its unique identifier in a message around the ring.
- When a node receives a message, it compares the received identifier with its own:
  - If the received ID is higher, it forwards the message.
  - If its own ID is higher, it sends its own ID instead.
  - If it receives its own ID, it declares itself the leader and informs others.

##### Pros

- **Simple**: Easy to implement in a ring topology.
- **Low message complexity**: In the best case, O(N) messages; in the worst case, O(N²).
- **Deterministic**: Always elects the node with the highest ID.

##### Cons

- **Ring dependency**: Requires a logical ring, which can break if a node fails.
- **Latency**: Message passing around the ring can be slow in large systems.
- **Assumes unique IDs**: Requires nodes to have distinct identifiers.

#### **Bully Algorithm**

##### How It Works

- A leader election algorithm where nodes have unique identifiers.
- When a node detects the leader has failed (or initiates an election), it sends an election message to all nodes with higher IDs.
- If no higher-ID node responds, it declares itself the leader and notifies others.
- If a higher-ID node responds, it takes over the election process.
- The node with the highest ID eventually becomes the leader.

##### Pros

- **Simple**: Straightforward to implement.
- **Robust**: Works in any topology, not limited to rings.
- **Deterministic**: Always elects the node with the highest ID.

##### Cons

- **High message complexity**: O(N²) in the worst case, as nodes may send messages to all higher-ID nodes.
- **Network overhead**: Frequent elections in unstable systems can flood the network.
- **High-ID node bias**: Always favors the node with the highest ID, which may not be optimal for load balancing.

#### Summary Table

| Algorithm       | Type                    | Pros                         | Cons                                | Message Complexity |
| --------------- | ----------------------- | ---------------------------- | ----------------------------------- | ------------------ |
| Central         | Mutual Exclusion        | Simple, low message overhead | Single point of failure, bottleneck | O(1) per request   |
| Ring-Based      | Mutual Exclusion/Leader | Simple, fair, no coordinator | High latency, fault intolerant      | O(N) per request   |
| Ricart-Agrawala | Mutual Exclusion        | Decentralized, fair          | High message overhead, latency      | O(N) per request   |
| Maekawa Voting  | Mutual Exclusion        | Lower message complexity     | Complex setup, deadlock risk        | O(√N) per request  |
| Chang-Roberts   | Leader Election         | Simple, deterministic        | Ring dependency, latency            | O(N) to O(N²)      |
| Bully           | Leader Election         | Simple, robust topology      | High message complexity, bias       | O(N²) worst case   |

#### Notes

- **Mutual Exclusion vs. Leader Election**: Central, Ring-Based, Ricart-Agrawala, and Maekawa are primarily for mutual exclusion (ensuring one node accesses a resource at a time), while Chang-Roberts and Bully are for leader election (selecting a coordinator node).
- **System Assumptions**: These algorithms assume reliable message delivery, unique node IDs, and sometimes specific topologies (e.g., ring for Chang-Roberts).
- **Scalability and Fault Tolerance**: Decentralized algorithms (Ricart-Agrawala, Maekawa) are more fault-tolerant but less scalable due to message overhead, while centralized and ring-based algorithms are simpler but less robust.
