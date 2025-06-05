Given $G =(V,E)$ a graph with $s \in V$ the source vertex, the BFS algorithm returns a tree containing all vertices reachable from s and $d(u) = \delta (s,u) upon termination, where $\delta (s,u)$ gives the length of the shortest simple path from s to u in G(that is, the number of edges needed to get from

s to u).

Proof. To prove this theorem we start by arguing that the following three

statements hold:

1. If d u k, vertex uis at level kof the BFS tree and δ s,u & k d u.

2. If Q v1v2 ...vr during the algorithm, we have d v1 & d v2 & ...&

d vr & d v1 1.

3. If v is dequeued before u, we have d v & d u.

The first statement is trivial. The second holds by noting that Q s at the

start and whenever we add a vertex v to Q when u is at the head of the

from statement 2.

queue, we have d v d u 1. The last statement follows immediately

The proof completes as follows. Assume the theorem does not hold and

let v be a vertex for which d v % δ s,v with δ s,v as small as possible.

Note, by statement 1 it is impossible to have d v $ δ s,v . Let u be the

last vertex on a shortest path from sto v. As δ s,v was chosen as small as

possible we have d u δ s,u δ s,v 1.

When uis dequeued there are two options. Either vwas dequeued earlier

and we have d v & d u (by statement 3). This yields d v & δ s,u &

δ s,v . Otherwise as u,v " E, the vertex v must be in the queue when u

is dequeued. Hence, by statement 2 we have d v & d u 1 δ s,v . Thus,

the theorem does not hold.

in both cases we have d v & δ s,v which contradicts the assumption that

The predecessor tree T N G V,E is defined as T Vπ < rsx,Eπ

with v " Vπ if π v © Nil and
