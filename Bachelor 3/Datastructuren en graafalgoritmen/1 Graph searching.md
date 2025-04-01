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

- **Goal**: Explore vertices level-by-level from a source $s$, by visiting neighbors $\Gamma(u)$ before neighbors of neighbors.
- **Data Structures**: Queue, color markers (WHITE, GRAY, BLACK), distance $d(u)$, parent $\pi(u)$.
- **Runtime**: $O(|V| + |E|)$.

### Key Theorems

- **Shortest Path Property**: $d(u) = \delta(s, u)$, the shortest path length from $s$ to $u$.
- **BFS Tree**: Forms a tree of all vertices reachable from $s$.

### Applications

1. **Bipartiteness Testing**: Assign levels and check for cross-level edges.
2. **Diameter Calculation**: Run BFS from all nodes (complexity $O(|V|(|V| + |E|))$).
3. **Shortest Path in Unweighted Graphs**: Directly use BFS distances.

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Pasted image 20250321161222.png]]

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

1. **Cycle Detection**: Presence of back edges indicates cycles.
2. **Topological Sorting**: Order nodes by decreasing $f(u)$.
3. **SCC Identification**: Via Kosaraju’s algorithm (two DFS passes).

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Pasted image 20250321161150.png]]

## 1.4 Topological Sorting in Directed Acyclic Graphs (DAGs)

### Definition and Purpose

A **topological sort** arranges vertices in a linear order where for every directed edge (u → v), vertex **u** precedes vertex **v**. This ordering is **only possible in directed acyclic graphs (DAGs)**, as cycles create unresolvable dependencies.

### Key Properties

- **DAG Exclusivity**: Impossible in cyclic graphs.
- **Non-Unique Orderings**: Multiple valid sequences may exist.
- **Dependency Resolution**: Ensures all directed relationships are honored.

### Algorithm Using Depth-First Search (DFS)

1. **DFS Traversal**: Perform DFS, marking each vertex’s discovery (`d[u]`) and finish times (`f[u]`).
2. **Order Generation**: Sort vertices by **decreasing finish times** to produce a topological order.

### Practical Applications

- **Project Scheduling**: Execute tasks with dependencies (e.g., course prerequisites).
- **Dynamic Programming**: Optimize path counting or resource allocation by processing nodes in topological order.

## 1.5 Strongly Connected Components (SCCs)

### Core Concepts

- **SCC Definition**: A maximal subset of vertices where every pair is mutually reachable via directed paths.
- **Condensation Graph**: Collapsing SCCs into single nodes forms a DAG.
- **Graph Partition**: Each vertex belongs to exactly one SCC.

### Kosaraju’s Algorithm for SCC Detection

1. **First DFS Pass**: Run DFS on the original graph to record finish times.
2. **Graph Reversal**: Construct the transpose graph (reverse all edges).
3. **Second DFS Pass**: Process nodes in **decreasing order of finish times** from the first DFS. Each DFS tree in the transposed graph represents an SCC.

### Algorithmic Insights

- **Runtime**: O(|V| + |E|) due to two DFS passes and linear-time reversal.
- **Edge Analysis**: Maximum edges between SCCs C₁ and C₂ = |C₁| × |C₂|.

### Applications

- **Network Analysis**: Identify clusters in social networks or functional groups in software dependencies.

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Pasted image 20250321161704.png]]

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
