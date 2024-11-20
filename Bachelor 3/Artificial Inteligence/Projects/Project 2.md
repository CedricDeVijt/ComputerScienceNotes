# 1 Bayesian Networks
## Factorization
a) Each variable has 2 possible states (binary). For 5 binary variables, there are $2^5 = 32$ entries in the joint probability table. Since the probabilities must sum to 1, we need **31** independent values to fully specify $P(O, G, S, F, I)$.

b) Using the Bayesian network structure the factorization of $P(O, G, S, F, I)$ is derived by applying the chain rule and using the conditional independencies encoded in the network:
$P(O, G, S, F, I) = P(G) \cdot P(S) \cdot P(O \mid G, S) \cdot P(F \mid S) \cdot P(I \mid O, F)$.

c) Each conditional probability table must be calculated based on the number of parent configurations for a node:
1. $P(G)$: $2 - 1 = 1$ value (1 binary variable).
2. $P(S)$: $2 - 1 = 1$ value.
3. $P(O \mid G, S)$: $2^2 \cdot (2 - 1) = 4$ values (2 parents, binary each).
4. $P(F \mid S)$: $2 \cdot (2 - 1) = 2$ values (1 parent).
5. $P(I \mid O, F)$: $2^2 \cdot (2 - 1) = 4$ values (2 parents).

Thus, the minimum number of probabilistic values required is **12**.

## Probability

a) $P(+b \mid +a)=0.5$
b) $P(+a, +b)= P(+a) \cdot P(+b \mid +a)= 0.25⋅0.5=0.125$
c) $P(+a \mid +b)= \frac{P(+a, +b)}{P(+b)}$
$P(+b)=P(+b∣+a)⋅P(+a)+P(+b∣−a)⋅P(−a) = (0.5⋅0.25)+(0.25⋅0.75)=0.3125$
$P(+a \mid +b)= \frac{P(+a, +b)}{P(+b)}= \frac{0.125}{0.3125}=0.4$
d) $P(−e, +a)= P(+a)⋅P(−e∣+a)$
$P(−e∣+a)=P(−e∣+b)⋅P(+b∣+a)+P(−e∣−b)⋅P(−b∣+a)=(0.75⋅0.5)+(0.9⋅0.5)=0.825$$P(−e,+a)=P(+a)⋅P(−e∣+a)=0.20625$

## Independence
a) $T⊥⊥Y$: Not Guaranteed
	There are two active paths: t->v->y and t->w->y
b) $T⊥⊥Y|W$: Not Guaranteed
	There is still an active path: t->w->y
c) $U ⊥⊥T$: Guaranteed
	The path u->x<-t is blocked by the collider x
d) $U ⊥⊥T |Z$: Not Guaranteed
	The path u->x<-t is not blocked by the x node because it's descendent is a conditioned node.
e) $Z ⊥⊥U$: Not Guaranteed
	The path z<-x<-u is an active path.
f) $Z ⊥⊥Y |V$: Not Guaranteed
	The path z<-x<-t->w->y is an active path.
g) $Z ⊥⊥Y |T, W$: Guaranteed
	The path z<-x<-t->w->y is blocked because the fork t is conditioned.
h) $Z ⊥⊥W$: Not Guaranteed
	The path z<-x<-t->w is an active path.

