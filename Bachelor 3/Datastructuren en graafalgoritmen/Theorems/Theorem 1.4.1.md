A directed acyclic graph $G$ can be sorted topologically by calling the DFS algorithm and adding the vertices in the order they are finished to the front of a linked list.

## Proof

Suppose we run the DFS algorithm on $G$ and $f( u)$ is the finishing time of a vertex $u \in V$. Thus, if $f (v) \lt f (u)$ , $u$ appears before $v$ in the linked list. Assume that $(u,v) \in E$, we need to show that $f (v) \lt f (u)$ . At some point we explore this edge from $u$ (which is Gray). At this time $v$ cannot be Gray as this would mean that $(u,v)$ is a back edge (contradicting Theorem 1.3.4). If $v$ is White, it is a descendant of $u$ with $d (u) \lt d (v)$, implying $f(v) \lt f(u)$ as required (due to the parenthesis Theorem). If $v$ is Black then $f (v) \lt f (u)$ as $u$ is still Gray.

$\blacksquare$
