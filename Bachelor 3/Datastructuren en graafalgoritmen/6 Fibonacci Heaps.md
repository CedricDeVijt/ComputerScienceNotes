## 6.1 Priority Queues & Network Optimization Algorithms

### Role in Graph Algorithms

**Why are priority queues critical for SP and MST algorithms?**

- Both Dijkstra's Shortest Path (SP) and Prim's Minimum Spanning Tree (MST) rely on efficiently managing vertex keys.
- **3-step procedure**:
  1. Maintain a priority queue on vertices.
  2. Initialize start vertex with key=0, others with ∞.
  3. Repeatedly extract minimum-key vertex and update neighbors' keys.

### Binary Heap Limitations

**What bottlenecks exist in classical implementations?**

- Binary heaps require O(log n) time for insert, delete-min, and decrease-key.
- For graphs with |E| ≥ |V|, total runtime becomes O(|E| log |V|).
- Fibonacci heaps optimize this by reducing decrease-key to O(1) amortized time.

## 6.2 Fibonacci Heap Structure & Operations

### Core Definition

**What defines a Fibonacci heap?**

- Collection of **heap-ordered trees** with:
  1. Roots in a doubly-linked list (root list).
  2. Minimum-key root accessed via pointer.
  3. Nodes track degree (child count) and mark status.

### Elementary Operations

#### Insert

- Create a single-node tree and add to root list: **O(1)** time.

#### Link

- Merge two trees by making one root a child of the other (based on keys): **O(1)** time.

#### Cut

- Remove a child node from its parent and promote it to the root list: **O(1)** time.

### Advanced Operations

#### Delete-Min

1. Remove min-key root and promote its children to the root list.
2. **Cleanup phase**: Link trees of equal degree using a degree array $B[1\ldots\lfloor\log n\rfloor]$.

- Worst-case O(n) time, but **amortized O(log n)** due to potential function.

#### Decrease-Key

1. Promote a node to root list if it violates heap order.
2. **Cascading cuts**: If a parent loses two children, promote it recursively.

- Amortized **O(1)** time due to marking strategy.

## 6.3 Amortized Analysis with Potential Method

### Potential Function Framework

**How does Φ(H) = t(H) + 2m(H) work?**

- $t(H)$: Number of trees in root list.
- $m(H)$: Number of marked nodes.
- Ensures amortized costs account for structural changes during operations.

### Delete-Min Analysis

- **Actual cost**: O(D(n) + t(H)), where $D(n)$ is max node degree.
- **Potential change**: After cleanup, roots ≤ $D(n) + 1$.
- Amortized cost becomes **O(D(n))** = O(log n).

### Decrease-Key Analysis

- **Actual cost**: O(c) for c cascading cuts.
- **Potential change**: $t(H)$ increases by c, $m(H)$ decreases by c-2.
- Net amortized cost: **O(1)**.

## 6.4 Bounding Maximum Node Degree

### Key Lemma

**Why is $size(x) ≥ φ^k$ for degree-k nodes?**

- Let $y_1, ..., y_k$ be children of $x$. Using Fibonacci sequence properties:
  - $size(x) ≥ F\_{k+2}$ (Fibonacci numbers).
  - $F\_{k+2} ≥ φ^k$ where $φ = (1+\sqrt{5})/2$.

### Degree Corollary

- Maximum degree $D(n) ≤ \lfloor\log_φ n\rfloor$ → **O(log n)**.
- Ensures delete-min’s cleanup phase remains efficient.

## 6.5 Applications & Exercises

### Algorithmic Impact

- Prim's MST and Dijkstra's SP achieve **O(|E| + |V| log |V|)** time with Fibonacci heaps.

### Practice Questions

1. **Union Operation**: Merge root lists of two heaps; **O(1)** amortized time.
2. **Max Root List Size**: After delete-min on 40-node heap, root list size ≤ $D(40) + 1 = \lfloor\log_φ 40\rfloor + 1 ≈ 6$.
3. **Alternative Potential Function**: Using $t(H) + m(H)$ increases amortized decrease-key cost to O(c), breaking O(1) bound.

---

## Key Points to Remember

- **Fibonacci Heap Advantage → Amortized Efficiency**: ★★★★★
  - Decrease-key in O(1), delete-min in O(log n).
- **Critical Structure → Cascading Cuts**: ★★★★☆
  - Prevents excessive tree depth by marking nodes losing children.
- **Bounding Degree → Fibonacci Sequence**: ★★★★☆
  - Ensures max degree grows logarithmically.
- **Potential Method → Φ(H) = t(H) + 2m(H)**: ★★★★☆
  - Balances cost of structural changes across operations.
- **Common Pitfall → Ignoring Amortized vs. Worst-Case**: ★★★☆☆
  - Single delete-min can take O(n), but amortized analysis justifies overall efficiency.
