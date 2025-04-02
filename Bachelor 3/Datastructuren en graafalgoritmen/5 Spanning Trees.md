## 5.1 Fundamental Properties of Trees and Spanning Trees

### Tree Definitions and Equivalent Properties

A **tree** is a connected graph where removing any edge disconnects it. Six equivalent characterizations include:

1. Unique paths between all vertices
2. No cycles with $e=n-1$ edges
3. Maximal acyclic (adding any edge creates a cycle)

#### Weighted Graphs and Spanning Trees

A **spanning tree** $T \subseteq G$ covers all vertices $V(G)$. In weighted graphs, the tree weight is $\alpha(T) = \sum_{e \in E(T)} \alpha(e)$. Minimizing $\alpha(T)$ solves real-world problems like network cost reduction.

## 5.2 Kruskal's Algorithm for Minimum Spanning Trees (MST)

### Algorithm Steps

1. Sort edges by non-decreasing weight.
2. Add edges to $T$ greedily, avoiding cycles (using disjoint-set data structures).

#### Cycle Detection via Disjoint Sets

- **FindSet(u)** checks if $u$ and $v$ belong to the same component.
- **Union(u,v)** merges components. Time: $O(|E|\log^*|V|)$ with path compression.

### Correctness Proof

- **Cycle avoidance** ensures $T$ is a tree.
- **Cut property**: Always selects the lightest edge across partitions, guaranteeing minimality.

### Time Complexity and Non-Uniqueness

- Sorting edges: $O(|E|\log|E|)$.
- MSTs are non-unique if multiple edges share the same weight.

## 5.3 Prim's Algorithm for MST

### Algorithm Steps

1. Initialize $U = \{v_1\}$ and track minimum edge weights to $U$.
2. Iteratively add the closest vertex to $U$ using a priority queue.

#### Key Data Structures

- **Binary heaps**: $O(|E|\log|V|)$ time.
- **Fibonacci heaps**: Optimized to $O(|E| + |V|\log|V|)$.

### Correctness via Cut Property

- At each step, the algorithm picks the lightest edge crossing the $(U, V-U)$ cut, ensuring MST validity.

### Runtime Comparisons

- **Dense graphs**: Prim's (Fibonacci heaps) outperforms Kruskal's.
- **Sparse graphs**: Kruskal's is faster due to efficient sorting.

## 5.4 Advanced MST Algorithms and Optimizations

### Graph Preprocessing for Sparse Graphs

- **Boruvka-like steps**: Contract components by adding cheapest edges.
- **Time savings**: Reduces graph size by ≥50% per iteration (Figure 16-17 [❓ Verify Context]).

### Fredman-Tarjan $O(|E|\log^*|V|)$ Algorithm

- **Hybrid approach**: Combines Prim’s steps with component contraction.
- **Termination**: Halts when $K_i \geq |V|$ after $\log^*|V|$ iterations.

---

## Key Points to Remember

- **Tree Equivalence → Acyclicity & Connectivity**: All 6 properties define trees. ★★★★★
- **Kruskal vs Prim → Data Structures Matter**: Kruskal’s for sparse, Prim’s for dense graphs. ★★★★☆
- **Light Edge Necessity**: MSTs only include light edges across cuts. ★★★★☆
- **Preprocessing Power**: Halving vertices speeds up MST computation. ★★★☆☆
- **Non-Uniqueness Caveat**: Equal-weight edges create multiple MSTs. ★★★☆☆
- **Fredman-Tarjan Trick**: $\log^*|V|$ iterations for near-linear time. ★★☆☆☆
