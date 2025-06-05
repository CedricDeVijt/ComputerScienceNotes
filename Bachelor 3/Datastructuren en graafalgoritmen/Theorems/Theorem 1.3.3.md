A DFS search of an undirected graph $G = (V,E)$ only encounters tree and back edges.

## Proof

Let $(u,v)$ be an arbitrary edge in $E$. Suppose that $v$ is Black when exploring the edge $(u,v)$ from $u$. This implies that $v$ has been discovered and all its outgoing edges have been explored. Thus, as $(u,v) \in E$, so is the edge $(v,u)$ and this edge must have been explored. At this time uwas either White or Gray (as it is still Gray) and hence the edge is either a tree or back edge.

$\blacksquare$
