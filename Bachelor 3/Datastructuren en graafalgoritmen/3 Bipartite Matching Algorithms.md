## 3.1 Graph Matching Basics

### Definitions

- **Matching**: A subset of edges $M \subseteq E$ in a graph $G = (V, E)$ where no two edges share a common vertex.
- **Maximum Matching**: A matching $M$ where no other matching $M'$ satisfies $|M'| > |M|$.
- **Bipartite Graph**: A graph $\bar{G} = (\bar{V}, \bar{E})$ partitioned into sets $L$ (left) and $R$ (right), with edges only between $L$ and $R$.

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Pasted image 20250321104854.png]]

## 3.2 Network Flow Solution for Bipartite Matching

### Flow Network Construction

- **Flow Graph $G$**:
  - $V = \bar{V} \cup \{s, t\}$.
  - Edges:
    - $\bar{E}$ directed from $L$ to $R$.
    - $(s, u)$ for $u \in L$.
    - $(v, t)$ for $v \in R$.
  - All edges have capacity 1.
- **Theorem 2.1**: A maximum flow in $G$ corresponds to a maximum matching in $\bar{G}$, with $|f| = |M|$.

### Algorithmic Approach

- **Ford-Fulkerson Method**:
  - Converts bipartite matching to max-flow problem.
  - Uses integer-valued flows (0 or 1 for edges).
  - Complexity: $O(|V||E|)$ using Edmonds-Karp (BFS for shortest augmenting paths).

## 3.3 Hopcroft-Karp Algorithm (1973)

### Key Concepts

- **Augmenting Path**: A path starting in an unmatched $L$-vertex, alternating between non-matching and matching edges, and ending in an unmatched $R$-vertex.
- **Symmetric Difference $M \oplus P$**: Swaps edges in a path $P$ to increase matching size by 1.

### Algorithm Steps

1. **Initialize**: $M = \emptyset$.
2. **Repeat**:
   - Find shortest augmenting paths using BFS to create a **layered graph**.
   - Use DFS to find a maximal set of vertex-disjoint shortest augmenting paths $P_1, \dots, P_k$.
   - Update $M \leftarrow M \oplus (P_1 \cup \dots \cup P_k)$.
3. **Terminate** when no more augmenting paths exist.

### Complexity Analysis

- **Iterations**: $O(\sqrt{|V|})$, as each phase increases the shortest augmenting path length.
- **Total Time**: $O(\sqrt{|V|} \cdot (|V| + |E|))$.

### Key Theorems

- **Lemma 3.1**: Symmetric difference with $k$ vertex-disjoint augmenting paths increases $|M|$ by $k$.
- **Theorem 3.2**: After augmenting with shortest paths, new shortest paths are strictly longer.
- **Lemma 3.2**: Maximum matching size is bounded by $|M| + |V|/l$, where $l$ is the shortest augmenting path length.

## 3.4 Applications and Exercises

### Hall’s Theorem

- **Statement**: A bipartite graph $G$ with $|L| = |R|$ has a perfect matching iff $|A| \leq |\Gamma(A)|$ for all $A \subseteq L$.
- **Proof Approach**: Use min-cut max-flow duality.

### Other Results

- **Regular Bipartite Graphs**: If every node has degree $d$, a perfect matching exists.
- **Dense Graphs**: If each vertex has $\geq n/2$ neighbors (for $|L| = |R| = n$), a perfect matching exists.
- **Vertex Cover**: Min vertex cover size equals max flow in the constructed network (Konig’s theorem).

---

## Key Points to Remember

- **Matching & Flow Equivalence**: Maximum bipartite matching is reducible to max-flow with unit capacities.
- **Hopcroft-Karp Complexity**: $O(\sqrt{|V|}|E|)$, leveraging BFS/DFS on layered graphs.
- **Augmenting Paths**: Symmetric difference with vertex-disjoint paths iteratively improves the matching.
- **Hall’s Condition**: Necessary and sufficient for perfect matchings in bipartite graphs.
- **Vertex Cover Duality**: Min vertex cover size equals max matching size in bipartite graphs (Konig’s theorem).
- **Ford-Fulkerson**: Guarantees integer flows for bipartite matching, enabling $O(|V||E|)$ solutions.
