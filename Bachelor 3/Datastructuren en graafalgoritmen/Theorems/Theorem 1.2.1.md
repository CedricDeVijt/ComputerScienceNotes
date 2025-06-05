Given $G =(V,E)$ a graph with $s \in V$ the source vertex, the BFS algorithm returns a tree containing all vertices reachable from s and $d(u) = \delta (s,u)$ upon termination, where $\delta (s,u)$ gives the length of the shortest simple path from $s$ to $u$ in $G$ (that is, the number of edges needed to get from $s$ to $u$).

## Proof

To prove this theorem we start by arguing that the following three statements hold:

1. If $d(u) = k$, vertex $u$ is at level $k$ of the BFS tree and $\delta (s,u) \leq k = d (u)$.
2. If $Q = v_1v_2 \dots v_r$ during the algorithm, we have $d(v_1) \leq d(v_2) \leq \dots \leq d(v_r) \leq d(v_1)+ 1$.
3. If $v$ is dequeued before $u$, we have $d(v) \leq d(u)$.

The first statement is trivial. The second holds by noting that $Q= s$ at the start and whenever we add a vertex $v$ to $Q$ when $u$ is at the head of the queue, we have $d(v)  = d(u) + 1$. The last statement follows immediately from statement 2.

The proof completes as follows. Assume the theorem does not hold and let $v$ be a vertex for which $d(v) \gt \delta (s,v)$ with $\delta (s,v)$ as small as possible.

Note, by statement 1 it is impossible to have $d(v) \gt \delta(s,v)$ . Let $u$ be the last vertex on a shortest path from $s$ to $v$. As $\delta(s,v)$ was chosen as small as possible, we have $d(u) = \delta(s,u) = \delta (s,v)-1$

When $u$ is dequeued there are two options. Either vwas dequeued earlier and we have $d(v) \leq d(u)$ (by statement 3). This yields $d(v) \leq \delta ( s,u) \leq \delta (s,v)$ . Otherwise as $(u,v) \in E$, the vertex $v$ must be in the queue when $u$ is dequeued. Hence, by statement 2 we have $d(v) \leq d(u)+1 = \delta (s,v)$ . Thus, in both cases we have $d(v) \leq \delta(s,v)$ which contradicts the assumption that the theorem does not hold.

$\blacksquare$