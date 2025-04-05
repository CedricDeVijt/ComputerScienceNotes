## 7.1 Single Source Shortest Path (SSSP) Fundamentals

### Problem Definition

**Key Components**: Directed weighted graph $G=(V,E)$, path weight $\alpha(p)=\sum \alpha(e)$, shortest path length $\delta(u,v)$.

- SSSP goal: Find $\delta(s,v)$ and shortest path tree $T_s$ from source $s$.
- **Critical distinction**: Problem becomes ill-defined if negative-weight cycles are reachable from $s$.

### Negative Cycle Implications

**Path Composition**: If a path includes a negative-weight cycle $C$, total weight $\alpha(p)$ can be made arbitrarily small by looping $C$.

- **Theorem 1.1**: Shortest paths exhibit optimal substructure (subpaths are shortest paths).
- **Key inequality**: $\delta(s,v) \leq \delta(s,u) + \alpha(u,v)$ for all edges $(u,v)$.

#### Cycle Analysis Example

- Path $s \to u \xrightarrow{k \times C} u \to v$ shows $\alpha(p)$ depends on $k\alpha(C)$. Negative $C$ makes $\alpha(p)$ unbounded below.

## 7.2 Relaxation Framework for SSSP

### Core Mechanism

**Initialize-Single-Source**: Set $d(s)=0$, $d(v)=\infty$ for $v \neq s$, $\pi(v)=\text{Nil}$.
**Relax$(u,v)$**: Update $d(v)=\min(d(v), d(u)+\alpha(u,v))$ and set $\pi(v)=u$ if improved.

### Theoretical Guarantees

- **Monotonicity**: $d(v)$ never increases and remains $\geq \delta(s,v)$.
- **Predecessor Graph $G\_\pi$**: Forms a tree rooted at $s$ if no negative cycles (Theorem 2.2).
- **Convergence**: After sufficient relaxations, $d(v)=\delta(s,v)$ (Theorem 2.1).

#### Cycle Detection Proof

- If $G\_\pi$ has cycle $C$, summing edge inequalities yields $\alpha(C) < 0$, contradicting no-negative-cycle assumption.

## 7.3 Dijkstra's Algorithm

### Algorithm Overview

**Greedy Strategy**: Maintain set $S$ of finalized vertices. Repeatedly extract $u$ with minimum $d(u)$, add to $S$, relax outgoing edges.

- **Assumption**: All edge weights $\geq 0$.
- **Time Complexity**: $O(|E|+|V|\log|V|)$ with Fibonacci heap.

### Correctness Proof

**Key Lemma**: When $u$ is added to $S$, $d(u)=\delta(s,u)$.

- **Inductive Argument**: First "wrong" vertex $u$ leads to contradiction via shortest path $p$ with predecessor $y$ having $d(y)=\delta(s,y) \leq d(u)$.

#### Failure Case Example

- **Graph with Negative Edge**: Dijkstra may incorrectly prioritize a longer path due to non-decreasing $d(v)$ updates.

## 7.4 Bellman-Ford Algorithm

### Iterative Relaxation

**Process**: Perform $|V|-1$ rounds of relaxing all edges.

- **Handles Negative Weights**: Detects reachable negative cycles via post-relaxation edge check.
- **Time Complexity**: $O(|V||E|)$.

### Correctness & Cycle Detection

- **Theorem 4.1**: After $|V|-1$ iterations, $d(v)=\delta(s,v)$ if no negative cycles.
- **Theorem 4.2**: Returns **FALSE** iff a reachable negative cycle exists.

#### Example: Late Convergence

- **Graph with $|V|=10$**: $d(v) > \delta(s,v)$ after $|V|-2=8$ iterations if a longer path requires $|V|-1$ relaxations.

## 7.5 Shortest Paths in DAGs

### Topological Order Advantage

**Algorithm**: Topologically sort vertices, relax edges in order.

- **Efficiency**: $O(|V|+|E|)$ due to single pass.
- **Theorem 5.1**: Correctness follows from path relaxation in topological order.

#### Critical Paths

- Longest paths in DAGs (via weight sign inversion) model scheduling dependencies.

## 7.6 Systems of Difference Constraints

### Constraint Graph Construction

**Mapping**: For $x_j - x_i \leq b_k$, create edge $(v_i, v_j)$ with weight $b_k$. Add source $v_0$ with 0-weight edges to all nodes.

- **Solution**: $x_i = \delta(v_0, v_i)$ if no negative cycles (Theorem 7.1).

### Applications & Extensions

- **Uniqueness**: Solutions form an equivalence class $(x_i + d)$.
- **Integer Solutions**: Requires $\delta(v_0, v_i)$ to be integers (non-trivial; may need rounding).

#### Equational Constraints

- $x_j = x_i + b_k$ translates to two inequalities: $x_j - x_i \leq b_k$ and $x_i - x_j \leq -b_k$.

## 7.7 All-Pairs Shortest Paths (APSP)

### Floyd-Warshall Algorithm

**Dynamic Programming**: Compute $\delta(i,j,k)$ for intermediate vertices $\{1, ..., k\}$.

- **Recurrence**: $\delta(i,j,k) = \min(\delta(i,j,k-1), \delta(i,k,k-1) + \delta(k,j,k-1))$.
- **Time**: $O(|V|^3)$.

### Johnson's Algorithm

**Reweighting Trick**: Use Bellman-Ford to compute $d(v)$, adjust weights to $\alpha_2(u,v) = \alpha(u,v) + d(u) - d(v)$.

- **Key Insight**: $\alpha_2 \geq 0$, enabling Dijkstra for APSP.
- **Complexity**: $O(|V||E| + |V|^2 \log |V|)$.

#### Example: Negative Weight Handling

- After reweighting, shortest paths remain preserved via $\alpha_2(p) = \alpha(p) + d(u) - d(v)$.

---

## Key Points to Remember

- **SSSP Basics→Optimal Substructure**: Shortest subpaths are themselves shortest. ★★★★☆
- **Dijkstra vs Bellman-Ford**: Non-negative vs arbitrary weights. Cycle detection critical. ★★★★★
- **Relaxation Framework→Monotonicity**: $d(v)$ converges downward to $\delta(s,v)$. ★★★★☆
- **Constraint Graphs→Bellman-Ford**: Systems of inequalities reduce to SSSP. ★★★☆☆
- **APSP→Floyd-Warshall vs Johnson**: Choose based on graph density and edge signs. ★★★★☆
- **Negative Cycles→NP-Hardness**: Shortest simple paths with negative cycles are NP-hard. ★★★☆☆
