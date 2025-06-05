The following algorithm, that relies on two DFS searches, computes the SCCs of a directed graph $G$.

1. Perform a DFS on $G$ and denote the finishing time of a node $u$ as $f (u)$
2. Construct the graph $G= (V,E)$, where $(u,v) \in E$ if and only if $(v,u) \in E$
3. Perform a DFS search on $G$, where the nodes of $G$ in the main for-loop of the DFS algorithm are ordered in decreasing value of $f (u)$

Each tree produced by the second DFS will correspond to a SCC.

## Proof

We start by defining $f (C)=  \text{max}_{u \in C} f (u)$ and $d(C) =  \text{min}_{u \in C} d (u)$ as the finishing time and discovery time of an SCC $C$ during the first DFS, respectively. We first show that if $(u,v) \in E$, $u \in C$ and $v \in C'$, where $C$ and $C'$ are two different SCCs, then $f (C) \gt f (C)$.

We distinguish two cases. First, assume $d (C) \lt d (C')$ and let $x$ be the first node of C that is discovered. Thus, at time $d (x)$ all the nodes in $C$ and $C'$ are still White. Further, as $(u,v) \in E$, all the nodes in $C$ and $C'$ are reachable from $x$, thus, due to the white path theorem, all the nodes in $C \lt C'$ are descendants of $x$. This implies that $f x f(C) \gt f(C')$ . In the second case, $d (C') \lt d (C)$ and by the white path theorem $f (x) = f (C')$ , where $x$ is the first node of $C$ that is discovered. Further, as $(u,v) \in E$, none of the vertices in $C$ are reachable from $x$ as this would imply that all the nodes in $C$ and $C'$ belong to the same SCC. Hence, $f (C) \gt f (C')$ as required. This implies that if $(u,v) \in E$, with $u$ and $v$ belonging to two different SCCs $C$ and $C'$, then $f (C) \lt f (C')$.

Now, assume by induction that the first $m$ trees produced by the second DFS search correspond to the first $m$ SCCs $C_1$ to $C_m$ such that $f (C_1) \gt \dots  f (C_m)$ . Denote $x$ as the root node of the next tree produced by the second DFS and denote $C$ as its SCC. Clearly, all the nodes in $C$ will be part of the tree rooted by $x$ (as they do not belong to $C_1 \lt \dots \lt C_m$ by induction). Further, as the vertices of $G$ in the main for-loop of the second DFS algorithm are ordered in decreasing value of $f (u)$ , we have $f( x) = f (C)$.

Next, suppose there exists an edge $(u,v) \in E'$, with $u \in C$ and $v \notin C_1 \cup \dots \cup C_m \cup C$, but part of SCC $C$. Let $y \in C'$ be the vertex with $f (y) = f (C)$ . Then, $f (x) = f (C) \lt f (C') = f (y)$ as shown earlier, but this is impossible as $f (x) \gt f (y)$ (as the nodes in the main for-loop of the second DFS were ordered in decreasing value of $f (u)$ ). As a result, tree $m + 1$ will consist of the nodes of $C$ only and therefore corresponds to the $m+ 1$-st SCC.
