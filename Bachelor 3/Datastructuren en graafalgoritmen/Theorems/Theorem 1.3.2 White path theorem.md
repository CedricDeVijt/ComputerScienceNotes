Given that we perform a DFS search on $G=(V,E)$ with $u,v \in V$, $v$ will be a descendant of $u$ in the DFS tree if and only if at time $d(u)$ there exists a White path from $u$ to $v$ in $G$.

## Proof

### $\Rightarrow$
Assume $v$ is a descendant of $u$ in the DFS tree and $w$ is a vertex on the path from $u$ to $v$ in this tree (and is therefore also a descendant of
$u$). By Parenthesis theorem, we have $d (u) \lt d (w)$ for all such vertices $w$, meaning at time $d (u)$ , $w$ is still White.

### $\Leftarrow$
Assume we have a white path from $u$ to $v$ at time $d (u)$ , but $v$ is not a descendant of $u$. Further, we can select $v$ such that $w$, the vertex just prior to $v$ on this path, is a descendant of $u$ in the DFS tree. Now, due to Parenthesis theorem, we have 

$$f(w) \lt f(u)$$

and as $v$ is White at time $d(u)$, we have

$$d(u) \lt d(v)$$

Now, either $v$ has been discoverd before $w$ explores the edge $(w,v)$ or it is discoverd at this time and thus before $w$ finishes; hence

$$d(v) \lt f(w) \lt f(u)$$

Combining the last two inequalities, we see that $v$ is after all a descendant of $u$ in the DFS tree, which contradicts our assumption.

$\blacksquare$