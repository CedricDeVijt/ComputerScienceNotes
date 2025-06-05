Given $G= (V,E)$ and $u,v \in V$, then either of the following two cases holds after running the DFS algorithm:

1. The intervals $[d(u), f(u)]$ and $[d (v) ,f (v)]$ do not overlap and $v$ is not a descendant of $u$.
2. The interval $[d (u) ,f (u)]$ completely engulfs the interval $[d (u) ,f (u)]$ and $v$ is a descendant of $u$ in the DFS tree/forest (or vice versa with the role of u and v switched).

Thus, $v$ is a descendant of $u$ if and only if $d(u) \lt d(v) \lt f(v) \lt f(u)$.

## Proof

Without loss of generality assume $d(u) \lt d (v)$. If $f(v) \lt d(v)$ then clearly both intervals are disjoint (there is no overlap) as $d(v) \lt f(v)$ and $v$ is not a descendant of $u$ in the DFS tree, because the descendants are exactly those vertices that are discovered while $u$ is Gray. If, on the other hand, $d(v) \lt f(u)$, we find that $v$ is discovered while $u$ is still Gray. Due to the recursive nature, $v$ will first explore all its neighbors (and turn Black) before $u$ can be finished; hence, $f(v) \lt f(u)$ as required.

$\blacksquare$
