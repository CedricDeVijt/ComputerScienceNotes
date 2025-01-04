# H1: Verzamelingen
## Wat is een aftelbare verzameling, bewijs $\mathbb{Q}$ is aftelbaar en $\mathbb{R}$ is niet aftelbaar. Is $\mathbb{N} \textrm{x} \mathbb{N}$ aftelbaar?
Een **aftelbare verzameling** is een verzameling waarvan de elementen in een bijectie kunnen worden geplaatst met de natuurlijke getallen $\mathbb{N}$. Dat betekent dat de verzameling eindig is, of oneindig maar dezelfde kardinaliteit heeft als $\mathbb{N}$, oftewel de verzameling is **denumerabel**.

### Bewijs dat $\mathbb{Q}$ aftelbaar is
De rationale getallen $\mathbb{Q}$ zijn de getallen die geschreven kunnen worden als $\frac{p}{q}$, waarbij $p, q \in \mathbb{Z}$ en $q \neq 0$. We moeten aantonen dat er een bijectie bestaat tussen $\mathbb{Q}$ en $\mathbb{N}$.

**Bewijs:**
1. We representeren $\mathbb{Q}$ als alle breuken $\frac{p}{q}$, waarbij $p \in \mathbb{Z}$ en $q \in \mathbb{N}$.
2. Orden alle paren $(p, q)$ in een rooster:
   - $p$ is op de horizontale as ($-3, -2, -1, 0, 1, 2, 3, \dots$).
   - $q$ is op de verticale as ($1, 2, 3, \dots$).

3. Door een zigzagpatroon te gebruiken, zoals het diagonale doorlopen van het rooster (Cantor-diagonalisatie), kunnen we alle paren $(p, q)$ opsommen.

4. We negeren dubbele vertegenwoordigingen van hetzelfde rationale getal (bijv. $\frac{1}{2} = \frac{2}{4}$) en breuken waarbij $p$ en $q$ geen relatief priem zijn.

5. Omdat er een opsomming mogelijk is van al deze breuken, en de dubbele elementen weggefilterd kunnen worden zonder de opsomming te onderbreken, is $\mathbb{Q}$ aftelbaar.

Conclusie: Er bestaat een bijectie tussen $\mathbb{Q}$ en $\mathbb{N}$, dus $\mathbb{Q}$ is aftelbaar.

### Bewijs dat $\mathbb{R}$ niet aftelbaar is
Het bewijs dat $\mathbb{R}$ niet aftelbaar is, wordt klassiek gedaan met het **diagonalisatie-argument van Cantor**.

**Bewijs:**
1. Veronderstel dat $\mathbb{R}$ aftelbaar is. Dat betekent dat alle reële getallen in het interval $[0, 1]$ opgesomd kunnen worden, bijv.:
   $$
   x_1 = 0.a_{11}a_{12}a_{13}\dots, \quad
   x_2 = 0.a_{21}a_{22}a_{23}\dots, \quad \dots
  $$
   waarbij $a_{ij}$ de $j$-de decimale cijfer van het $i$-de getal is.

2. Bouw een nieuw getal $y$ door diagonaal door deze lijst te gaan en de $j$-de decimale cijfer van $x_j$ te wijzigen. Stel:
   $$
   b_j = 
   \begin{cases} 
   1 & \text{als } a_{jj} \neq 1, \\
   2 & \text{als } a_{jj} = 1.
   \end{cases}
  $$
   Het nieuwe getal $y = 0.b_1b_2b_3\dots$ verschilt in elk cijfer $b_j$ van $x_j$.

3. Het getal $y$ zit niet in de oorspronkelijke lijst, wat in tegenspraak is met de veronderstelling dat $\mathbb{R}$ aftelbaar is.

Conclusie: $\mathbb{R}$ is niet aftelbaar.

### Is $\mathbb{N} \times \mathbb{N}$ aftelbaar?
Ja, $\mathbb{N} \times \mathbb{N}$ is aftelbaar. We bewijzen dit door een opsomming te construeren:

**Bewijs:**
1. Elk element van $\mathbb{N} \times \mathbb{N}$ kan worden gezien als een paar $(m, n)$, waarbij $m, n \in \mathbb{N}$.
2. Orden de paren $(m, n)$ in een rooster met $m$ op de horizontale as en $n$ op de verticale as.
3. Door het rooster diagonaal door te lopen (zoals Cantor-diagonalisatie), kunnen we alle paren opsommen:
   - Eerst $(0, 0)$,
   - Dan $(1, 0), (0, 1)$,
   - Dan $(2, 0), (1, 1), (0, 2)$, enzovoort.
4. Deze opsomming geeft een bijectie tussen $\mathbb{N} \times \mathbb{N}$ en $\mathbb{N}$.

Conclusie: $\mathbb{N} \times \mathbb{N}$ is aftelbaar.

# H2: Relaties en functies
## Wat is een partieel geordende verzameling? Wat is reflexief, anti-symmetrisch, transitief (symbolisch), stel een gegeven verzameling, toon aan dat deze reflexief, anti-symmetrisch en of transitief is. Is dit een totale orde? Wat is minima en minimaal element? Stel $v = 2^x$ en $x = {a, b, c}$: Bewijs dat dit een partiële ordening is.


## Wat is een functie en een injectieve functie (in symbolen)? Neem $f$, $g$ injectief, bewijs dat $f \circ g$ injectief is of geef een tegenvoorbeeld als dit niet altijd zo is.
## Wat is een relatie, equivalentierelatie en equivalentieklasse? Toon aan dat twee verschillende equivalentieklassen disjunct zijn.
## Geef de definitie van een relatie, equivalentieklassen en een partitie. Toon aan dat alle equivalentierelaties partities zijn.
## Wat is een functie en een injectieve functie (in symbolen)? Neem $f$, $g$ injectief, bewijs dat $f \circ g$ injectief is of geef een tegenvoorbeeld als dit niet altijd zo is.

# H3: Bewijstechnieken
## (3x) Bewijs via inductie het Binomium van Newton.
## Wat is inductie? Geef alle verschillende soorten inductie. Bewijs via inductie: $\sum_{i=0}^n k^2 = \frac{n(n+1)(2n+1)}{6}$.

# H4: Tellen

# H5: Kansrekening
## Wat is een poisson verdeling (symbolisch)? Leid de verwachtingswaarde af. Wat is een toevalsveranderlijke. Bewijs $E(x+y) = ?$. Bewijs voor hetzelfde ook de var.
## Wat is een poissonverdeelde toevalsveranderlijke? Wat is de variantie ervan? Bewijs.
## Wat is een normaalverdeelde toevalsveranderlijke? Hoe en wanneer kunnen we hier een binomiale verdeling mee benaderen?
## Wat is de formule voor de variantie van een binomiale verdeling? Bewijs.
## Bewijs $E[x+y]$ en $var(x+y)$ en geef de voorwaarde hiervoor. 
## Wat is een toevalsveranderlijke? Toon aan dat de som van $X$ ~ $NB(n, p)$: $P(X_i) = 1$.
## Leg de paradox van Simpson uit met een voorbeeld.
## Wat is een binomiaal verdeelde toevalsveranderlijke? Bewijs E(x).
## Bewijs de regel van Bayes en de somregel.
## Wat is een toevalsveranderlijke? Toon aan dat de som van $X$ ~ $NB(n, p)$: $P(X_i) = 1$.
## Gegeven twee poissonverdelingen $P(\lambda 1), P(\lambda 2)$. Bewijs dat $P(\lambda 1 + \lambda 2) = k$ en dat dit nog steeds poissonverdeeld is.

# H6: Boolean algebra
## (2x) Wat is het dualiteitsprincipe? Leg uit a.d.h.v. de terminologie. Toon aan en geef alle definities die in deze eigenschap voorkomen (verduidelijk).

# H7: Genererende functies
## $\sum_{k=0}^{n} k*\binom{n}{k}$. Geef een gesloten formule hiervoor en bewijs.
## Genererende functies: Reken een rijtje uit. (Je kreeg een rij, maar er kwamen geen getallen in voor, enkel symbolen)
## Wat is een genererende functie en de inverse ervan? Wanneer bestaat de inverse niet? Bewijs.
## $S_0, a, b$ gegeven: Geef de niet-recursieve formule voor $S_n = a S_{n-1} + b$. Bewijs.
## $\sum_{k=0}^{n} k*\binom{n}{k}$. Geef een gesloten formule hiervoor en bewijs.
## $S_0, a, b$ gegeven: Geef de niet-recursieve formule voor $S_n = a S_{n-1} + b$. Bewijs.

# Niet voor 2024
## Geef de wet van grote getallen en bewijs. Geef ook Chebychev.