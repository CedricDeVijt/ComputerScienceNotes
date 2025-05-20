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

# 8 Election Mechanisms

## 8.6 Chang-Roberts Ring Algorithm

**Elect highest-ID process via token circulation**.

- **Process Flow**:
  - Forward Election(ID) if received ID < own ID.
  - Declare self leader if token completes full circle.

### Safety & Liveness

- **Safety**: Unique IDs prevent multiple leaders.
- **Liveness**: Guaranteed in failure-free, asynchronous systems.

### Efficiency

- **Bandwidth**: $O(N)$ to $O(N^2)$ messages.
- **Turnaround Time**: $O(N\delta)$.

## 8.7 Bully Algorithm

**Timeout-based leader election with crash recovery**.

- **Process Flow**:
  1. Send Election to higher-ID processes.
  2. If no Answer, declare self leader.
  3. Broadcast Coordinator to lower IDs.

### Crash Handling

- Higher-ID processes "bully" lower IDs into submission.

### Efficiency

- **Worst-Case Bandwidth**: $O(N^2)$ messages.
- **Turnaround Time**: Dependent on timeout $T$.

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
- **Common Pitfall**: Assuming reliable networks for liveness [❓ Verify Context].
