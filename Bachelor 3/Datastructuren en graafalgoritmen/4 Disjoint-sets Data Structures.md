## 4.1 Linked-List Representation of Disjoint-Sets

### Operations

- **MakeSet(x)**: Creates a set containing only $x$ ($O(1)$ time). $x$ becomes the representative.
- **FindSet(x)**: Returns the representative of the set containing $x$ ($O(1)$ time via root pointer).
- **Union(x, y)**: Merges the sets containing $x$ and $y$. Appends the shorter list to the longer one to minimize root pointer updates.

### Time Complexity Analysis

- **Theorem 1.1**: A sequence of $m$ operations (including $n$ MakeSet) has a worst-case cost of $O(m + n \log n)$.
  - **Proof**: Each item’s root pointer is updated $≤ log_2 n$ times (doubling set size with each update). Total Union cost is $O(n \log n)$.

### Drawbacks Without Optimization

- Appending lists arbitrarily (ignoring length) can lead to $\Theta(m^2)$ time. Example: Repeatedly merging single-element sets into a growing list.

## 4.2 Disjoint-Sets Forest (Tree Representation)

### Structure

- Each set is a tree. Representative is the root. Each node points to its parent.
- **Union by Rank**: Merge smaller-rank trees into larger-rank trees to limit tree height.
- **Path Compression**: During FindSet, flatten paths by pointing nodes directly to the root.

### Time Complexity Without Path Compression

- **Theorem 2.1**: Worst-case cost for $m$ operations is $O(m \log n)$.
  - **Proof**: Tree height $≤ log_2n$ (since rank increases only when merging equal-rank trees).

### Time Complexity With Path Compression

- **Theorem 2.2**: Worst-case cost reduces to $O(m α(m, n))$, where $\alpha$ is the inverse Ackermann function (effectively ≤ 4 in practice).
  - **Proof Sketch**:
    - Partition ranks into blocks based on $\log_*$ (iterated logarithm).
    - Block costs ($O(m \log_* n)$) and path costs ($O(n \log_* n)$) dominate.

### Key Heuristics

1. **Union by Rank**: Ensures tree height grows logarithmically.
2. **Path Compression**: Accelerates future FindSet operations.

## 4.3 Union-by-Weight vs Union-by-Rank

- **Union-by-Weight**: Merge smaller sets into larger ones (based on size).
- **Non-Equivalence**: Union-by-rank focuses on tree height, while union-by-weight uses set size. Worst-case FindSet time remains $O(\log n)$ for both, but structures differ.

## 4.4 Applications and Algorithms

### Cycle Detection in Graphs

- **Algorithm** (from Exercise 5):
  1. Initialize sets for all vertices.
  2. For each edge $(u, v)$, check if $FindSet(u) == FindSet(v)$. If yes, return `False` (cycle detected).
  3. Union sets if no cycle.
- **Efficiency**: Use disjoint-sets forest with path compression and union by rank for $O(\alpha(|E|, |V|))$ time per operation.

### Connected Components

- **Algorithm**: Use disjoint-sets to track components. Number of MakeSet, Union, and FindSet operations is $O(|V| + |E| \alpha(|V|))$.

## Key Points to Remember

- **Linked-List vs Forest**:
  - Linked-list: $O(1)$ FindSet, $O(n \log n)$ Union (with optimization).
  - Forest: $O(α(n))$ amortized time per operation with path compression + union by rank.
- **Union Heuristics**:
  - Union by rank/path compression ensures near-linear time complexity.
  - Union-by-weight is not equivalent to union-by-rank but achieves similar asymptotic bounds.
- **Path Compression**:
  - Flattens tree during FindSet, drastically reducing future access time.
- **Inverse Ackermann Function**:
  - α(m, n) grows extremely slowly, making disjoint-sets forest practically optimal.
- **Cycle Detection**:
  - Disjoint-sets forest is optimal for Kruskal’s algorithm and cycle checking in graphs.

## Useful resources

[Disjoint Set Data Structures](https://www.geeksforgeeks.org/disjoint-set-data-structures/)
[Disjoint Set Union](https://cp-algorithms.com/data_structures/disjoint_set_union.html)
