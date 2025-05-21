## Theorem

Any nondeterministic TM that uses $f(n)$ space can be converted to a deterministic TM that uses only $f^2(n)$ space.

$\forall f:\mathbb{N} \to \mathbb{R}^+,\ \forall n \in \mathbb{N},\ f(n) \geq n: NSPACE(f(n)) \subseteq SPACE(f^2(n))$

## Proof

Let N be an NTM deciding a language A in space f(n). We construct a deterministic TM M deciding A. Machine M uses the procedure CANYIELD, which tests whether one of N’s configurations can yield another within a specified number of steps. Let w be a string considered as input to N. For configurations c1 and c2 of N, and integer t, CANYIELD(c1,c2,t) outputs accept if N can go from configuration c1 to configuration c2 in t or fewer steps along some nondeterministic path. If not, CANYIELD outputs reject. For convenience, we assume that tis a power of 2.

CANYIELD = On input c1, c2, and t:
1. If t = 1, then test directly whether c1 = c2 or whether c1 yields c2 in one step according to the rules of N. Accept if either test
succeeds; reject if both fail.
2. If t>1, then for each configuration cm of N using space f(n):
3. Run CANYIELD(c1,cm, t2 ).
4. Run CANYIELD(cm,c2,t2 ).
5. If steps 3 and 4 both accept, then accept.
6. If haven’t yet accepted, reject.
