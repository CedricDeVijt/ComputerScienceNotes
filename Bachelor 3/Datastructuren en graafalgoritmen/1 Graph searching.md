## 1.1 Graph Representations

### Definitions

- **Graph**: $G = (V, E)$, where $V$ is a set of vertices and $E$ is a set of edges.
- **Directed vs. Undirected**: Edges have direction in directed graphs; undirected edges are bidirectional.
- **Adjacency List**:
  - Array of lists, where each list contains neighbors of a vertex.
  - **Pros**: $O(|E|)$ space for sparse graphs. **Cons**: Edge check in $O(\text{degree}(u))$.
- **Adjacency Matrix**:
  - $|V| \times |V|$ matrix with 1 at $(u, v)$ if $(u, v) \in E$.
  - **Pros**: Edge existence check in $O(1)$. **Cons**: $O(|V|^2)$ space.

![[Pasted image 20250214111039.png]]

## 1.2 Breadth-First Search (BFS)

### Algorithm Overview

- **Goal**: Explore vertices level-by-level from a source $s$.
- **Data Structures**: Queue, color markers (WHITE, GRAY, BLACK), distance $d(u)$, parent $\pi(u)$.
- **Runtime**: $O(|V| + |E|)$.

### Key Theorems

- **Shortest Path Property**: $d(u) = \delta(s, u)$, the shortest path length from $s$ to $u$.
- **BFS Tree**: Forms a tree of all vertices reachable from $s$.

### Applications

1. **Bipartiteness Testing**: Assign levels and check for cross-level edges.
2. **Diameter Calculation**: Run BFS from all nodes (complexity $O(|V|(|V| + |E|))$).
3. **Shortest Path in Unweighted Graphs**: Directly use BFS distances.

![[Pasted image 20250221112312.png|500]]![[Pasted image 20250221112336.png|500]]

## 1.3 Depth-First Search (DFS)

### Algorithm Overview

- **Goal**: Explore vertices deeply before backtracking.
- **Timestamps**: Discovery time $d(u)$, finish time $f(u)$.
- **Edge Classification**:
  - **Tree edges**: Part of DFS forest.
  - **Back edges**: Connect to ancestors (detect cycles).
  - **Forward/Cross edges**: Connect to descendants/non-ancestors.

### Key Theorems

- **Parenthesis Theorem**: Intervals $[d(u), f(u)]$ are nested or disjoint.
- **White Path Theorem**: $v$ is a descendant of $u$ iff a white path exists from $u$ to $v$ at $d(u)$.

### Applications

4. **Cycle Detection**: Presence of back edges indicates cycles.
5. **Topological Sorting**: Order nodes by decreasing $f(u)$.
6. **SCC Identification**: Via Kosaraju’s algorithm (two DFS passes).

## 1.4 Topological Sorting

- A linear ordering of all vertices in a directed acyclic graph (DAG) such that for every directed edge $(u, v)$, vertex $u$ comes before vertex $v$ in the ordering.

- **Properties**:

  - Only possible for DAGs (graphs with no cycles).
  - Not unique - multiple valid topological orderings may exist.
  - Represents a valid sequence that respects all dependencies.

- **Intuition**: If we view edges as dependencies (e.g., $(u, v)$ means "$u$ must come before $v$"), a topological sort gives an order that satisfies all dependencies simultaneously.

### Algorithm

- **Step 1**: Run DFS and record finish times.
- **Step 2**: Sort nodes in decreasing order of $f(u)$.

### Applications

7. **Task Scheduling**: Ensure dependencies are respected.
8. **Path Counting**: Use dynamic programming on topological order.

## 1.5 Strongly Connected Components (SCCs)

- **Definition**: A strongly connected component (SCC) in a directed graph is a maximal set of vertices C ⊆ V such that for every pair of vertices u and v in C, there exists a path from u to v and a path from v to u.

- **Properties**:
  - **Maximality**: No additional vertex can be included in an SCC without breaking its property of mutual reachability.
  - **Partition of Graph**: The SCCs of a graph partition the vertex set, meaning every vertex belongs to exactly one SCC.
  - **Condensation Graph**: Collapsing each SCC into a single node produces a directed acyclic graph (DAG), which highlights the structure between components.
  - **Mutual Reachability**: Within each SCC, every vertex is reachable from every other vertex.

### Kosaraju’s Algorithm

9. **Step 1**: Run DFS on $G$, record $f(u)$.
10. **Step 2**: Reverse $G$ to form $G'$.
11. **Step 3**: Run DFS on $G'$ in decreasing order of $f(u)$.

- **Runtime**: $O(|V| + |E|)$.

### Key Insights

- SCCs form subtrees in DFS forests.
- **Max SCC Edges**: For two SCCs $C_1, C_2$, max edges = $|C_1| \cdot |C_2|$.

---

## Key Points to Remember

- **Adjacency Matrix vs. List**: Matrix for dense graphs (fast edge checks), List for sparse graphs (space-efficient).
- **BFS**: Finds shortest paths in unweighted graphs; uses a queue.
- **DFS**: Classifies edges; detects cycles via back edges; timestamps for ordering.
- **Topological Sort**: Valid only for DAGs; order nodes by $f(u)$.
- **SCCs**: All nodes mutually reachable; Kosaraju’s algorithm uses reversed graph and DFS.
- **Runtime Complexities**:
  - BFS/DFS: $O(|V| + |E|)$.
  - Universal Sink Detection: $O(|V|)$.
  - Kosaraju’s Algorithm: $O(|V| + |E|)$.
