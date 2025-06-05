A directed graph $G$ contains no cycles if a DFS traversal of the graph does not encounter a back edge.

## Proof

Clearly, if the DFS tree contains a back edge, then $G$ contains a cycle. The reverse statement can be proven as follows. Assume $C$ is a cycle with vertices $u_1, \dots ,u_k$ in $G$ and without loss of generality, let $u_1$ be the first vertex on $G$ that is discovered by the DFS search. Then, by the white path theorem, the entire cycle is part of the DFS tree of $u_1$, including $u_k$. When we we visit $u_k$, we will explore the edge $(u_k,u_1)$ and this edge is a back edge as $u_1$ was already discovered at that time (but not finished as $u_k$ is a descendant of $u_1$).

$\blacksquare$
