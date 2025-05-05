## PROOF IDEA

We prove this theorem by presenting a polynomial time algorithm that decides PATH. Before describing that algorithm, let’s observe that abrute-force algorithm for this problem isn’t fast enough.

A brute-force algorithm for PATH proceeds by examining all potential paths in Gand determining whether any is a directed path from sto t. A potential pathis a sequence of nodes in Ghaving a length of at most m, where mis the numberof nodes in G. (If any directed path exists from sto t, one having a length of atmost mexists because repeating a node never is necessary.) But the number ofsuch potential paths is roughly mm, which is exponential in the number of nodesin G. Therefore, this brute-force algorithm uses exponential time

To get a polynomial time algorithm for PATH, we must do something thatavoids brute force. One way is to use a graph-searching method such as breadthfirst search. Here, we successively mark all nodes in Gthat are reachable from sby directed paths of length 1, then 2, then 3, through m. Bounding the runningtime of this strategy by a polynomial is easy.

## PROOF

A polynomial time algorithm M for PATH operates as follows.
M=“On input ⟨G,s,t⟩, where Gis a directed graph with nodes sand t:

1. Place a mark on node s.
2. Repeat the following until no additional nodes are marked:
3. Scan all the edges of G. If an edge (a,b) is found going froma marked node ato an unmarked node b, mark node b.
4. If tis marked, accept. Otherwise, reject.

Now we analyze this algorithm to show that it runs in polynomial time. Obviously, stages 1 and 4 are executed only once. Stage 3 runs at most m timesbecause each time except the last it marks an additional node in G. Thus, thetotal number of stages used is at most 1 + 1 + m, giving a polynomial in the sizeof G.

Stages 1 and 4 of M are easily implemented in polynomial time on any reasonable deterministic model. Stage 3 involves a scan of the input and a test ofwhether certain nodes are marked, which also is easily implemented in polynomial time. Hence M is a polynomial time algorithm for PATH.
