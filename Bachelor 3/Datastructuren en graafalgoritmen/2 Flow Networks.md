## 2.1 Definitions and Basic Properties

### Flow Network

- A **flow network** $G = (V, E)$ is a directed graph with:
  - **Source** $s$ and **sink** $t$.
  - Edge capacities $c(u,v) \geq 0$.
  - All nodes $v \in V$ lie on a path from $s$ to $t$.

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Network_Flow_Cropped2_-_revised.png]]

### Flow

- A **flow** $f$ is a function $V \times V \rightarrow \mathbb{R}$ satisfying:
  1. **Capacity constraint**: $f(u,v) \leq c(u,v)$.
  2. **Skew symmetry**: $f(u,v) = -f(v,u)$.
  3. **Flow conservation**: $\sum\limits_{v \in V} f(u,v) = 0$ for $u \in U \setminus \{s,t\}$.
- **Value of flow** $|f| = \sum\limits_{v \in V} f(s,v)$.

### Multiple Sources/Sinks Reduction

- Convert multiple sources/sinks to a single source/sink by:
  - Adding a super-source $s$ with edges $(s, s_i)$ of infinite capacity.
  - Adding a super-sink $t$ with edges $(t_j, t)$ of infinite capacity.

## 2.2 Ford-Fulkerson Method

### Residual Network

- **Residual network** $G_f = (V, E_f)$:
  - Residual capacity $c_f(u,v) = c(u,v) - f(u,v)$.
  - Edges $(u,v) \in E_f$ if $c_f(u,v) > 0$.

### Augmenting Paths

- An **augmenting path** is a simple $s$-$t$ path in $G_f$.
- **Corollary 2.1**: Augmenting along $p$ increases $|f|$ by $c_f(p)$.

### Algorithm Steps

1. Initialize $f(u,v) = 0$.
2. While an augmenting path $p$ exists in $G_f$:
   - Augment $f$ by $c_f(p)$.
3. Return $f$.

### Max-Flow Min-Cut Theorem

- **Theorem 2.1**: The following are equivalent:
  1. $f$ is a maximum flow.
  2. $G_f$ has no augmenting paths.
  3. $|f| = c(S,T)$ for some cut $(S,T)$.

## 2.3 Performance of Ford-Fulkerson

### Termination Issues

- Fails to terminate for irrational capacities (e.g., Figure 8 with $r = (\sqrt{5}-1)/2$).
- **Rational capacities**: Terminates by scaling to integers.

![[Bachelor 3/Datastructuren en graafalgoritmen/images/Pasted image 20250314110413.png]]

### Edmonds-Karp Algorithm

- Uses BFS to find shortest augmenting paths.
- **Time complexity**: $O(|V||E|^2)$.
- **Lemma 4.1**: Shortest-path distances monotonically increase.

## 2.4 Preflow-Push Algorithms

### Preflow Definition

- **Preflow**: Relaxed flow with:
  1. Capacity and skew symmetry constraints.
  2. **Excess flow** $e(u) = \sum_{v \in V} f(v,u) \geq 0$.

### Operations

- **Push**: Send flow from overflowing $u$ to $v$ if $h(u) = h(v) + 1$.
- **Lift**: Increase $h(u)$ if $u$ overflows and no eligible $v$ exists.

### Algorithm Steps

4. Initialize heights $h(s) = |V|$, $h(u) = 0$.
5. Saturate edges from $s$.
6. Repeatedly push/lift until no overflowing nodes.

### Performance

- **Time complexity**: $O(|V|^2|E|)$.
- **Key Lemmas**:
  - Heights are bounded by $2|V| - 1$.
  - $O(|V|^2|E|)$ operations (pushes/lifts).

## 2.5 Key Theorems and Lemmas

### Flow Conservation Lemma (Lemma 2.2)

- For any cut $(S,T)$, $|f| = f(S,T) \leq c(S,T)$.

### Max-Flow Min-Cut Equivalence

- Proof via residual network analysis and cut capacity.

### Goldberg’s Preflow-Push Correctness

- Terminates with no excess flow, yielding a maximum flow.

## 2.6 Exercises and Applications

### Edge/Vertex Connectivity

- $\lambda(G)$ (edge connectivity) via $|V|$ max-flow computations.
- $\kappa(G)$ (vertex connectivity) via $O(|V|\kappa(G))$ max-flow runs.

## Key Points to Remember

- **Flow Network**: Directed graph with capacities, source, and sink.
- **Flow Constraints**: Capacity, skew symmetry, conservation.
- **Residual Network**: Represents remaining capacity after flow $f$.
- **Augmenting Path**: Path in $G_f$ increasing flow value.
- **Max-Flow Min-Cut**: Equivalence between max flow and min cut.
- **Ford-Fulkerson**: May not terminate for irrational capacities.
- **Edmonds-Karp**: $O(|V||E|^2)$ via BFS for shortest paths.
- **Preflow-Push**: $O(|V|^2|E|)$, uses height labels and push/lift operations.
- **Critical Edges**: Increasing/decreasing capacity affects max flow.
- **Applications**: Connectivity, matrix problems, scheduling.
