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
## Wat is een partieel geordende verzameling? Wat is reflexief, anti-symmetrisch, transitief (symbolisch), stel een gegeven verzameling, toon aan dat deze reflexief, anti-symmetrisch en of transitief is. Is dit een totale orde? Wat is minimaal en minimaal element? Stel $v = 2^x$ en $x = {a, b, c}$: Bewijs dat dit een partiële ordening is.
Een **partieel geordende verzameling** (of poset, *partially ordered set*) is een verzameling $P$ samen met een binaire relatie $\leq$ die voldoet aan de volgende eigenschappen:

1. **Reflexiviteit**: Voor alle $x \in P$, geldt $x \leq x$.  
2. **Anti-symmetrie**: Voor alle $x, y \in P$, als $x \leq y$ en $y \leq x$, dan $x = y$.  
3. **Transitiviteit**: Voor alle $x, y, z \in P$, als $x \leq y$ en $y \leq z$, dan $x \leq z$.  

Als een relatie aan deze drie voorwaarden voldoet, noemen we de relatie een **partiële ordening** en noemen we $(P, \leq)$ een partieel geordende verzameling.

Een **totale orde** is een speciale vorm van een partiële ordening, waarbij elk paar elementen vergelijkbaar is. Dit betekent dat voor alle $x, y \in P$, geldt $x \leq y$ of $y \leq x$. Als niet alle elementen vergelijkbaar zijn, is het geen totale orde.

### Voorbeeld

Laten we een verzameling $X = \{a, b, c\}$ nemen en een binaire relatie $\leq$ definiëren:  
$$
a \leq b, \quad b \leq c, \quad a \leq c.
$$

#### Eigenschappen:
1. **Reflexief**: Elk element is gerelateerd aan zichzelf ($a \leq a, b \leq b, c \leq c$).
2. **Anti-symmetrisch**: Als $x \leq y$ en $y \leq x$, dan $x = y$. Hier is dit waar, want er zijn geen cirkels of situaties waarin $x \neq y$ en $x \leq y$ en $y \leq x$.
3. **Transitief**: Als $a \leq b$ en $b \leq c$, dan $a \leq c$. Dit geldt voor de gegeven relatie.

Dus deze relatie $\leq$ is een **partiële ordening**. Als we verder aannemen dat $a, b, c$ allemaal vergelijkbaar zijn ($a \leq b \leq c$), dan is het ook een **totale ordening**.

### Minima en minimaal element
1. **Minimaal element**: Een element $m \in P$ is minimaal als er geen ander $x \in P$ is zodat $x \leq m$ en $x \neq m$.
2. **Minimum (of kleinste element)**: Een element $m \in P$ is het minimum als $m \leq x$ voor alle $x \in P$.

### Stel $v = 2^x$ en $x = \{a, b, c\}$

Neem de verzameling $V = \{2^a, 2^b, 2^c\}$ en definieer een relatie $\leq$ als:  
$$
2^x \leq 2^y \iff x \leq y.
$$

#### Bewijs dat dit een partiële ordening is:
1. **Reflexiviteit**: Voor $x \in \{a, b, c\}$, geldt $2^x \leq 2^x$, want $x \leq x$.
2. **Anti-symmetrie**: Als $2^x \leq 2^y$ en $2^y \leq 2^x$, dan $x = y$, dus $2^x = 2^y$.
3. **Transitiviteit**: Als $2^x \leq 2^y$ en $2^y \leq 2^z$, dan $2^x \leq 2^z$, want $x \leq y$ en $y \leq z$ impliceren $x \leq z$.

Daarom is $(V, \leq)$ een **partiële ordening**.

#### Is dit een totale ordening?
Als $a, b, c$ niet vergelijkbaar zijn, is $\leq$ geen totale orde. Bijvoorbeeld, als $a$ en $b$ niet met elkaar in relatie staan, dan kunnen $2^a$ en $2^b$ ook niet met elkaar vergeleken worden.

#### Minimum en minimaal element:
- **Minimum**: Als $a \leq b$ en $a \leq c$, dan is $2^a$ het minimum.
- **Minimaal element**: Als $a$ niet door een ander element voorafgegaan wordt, is $2^a$ minimaal.

## Wat is een functie en een injectieve functie (in symbolen)? Neem $f$, $g$ injectief, bewijs dat $f \circ g$ injectief is of geef een tegenvoorbeeld als dit niet altijd zo is.

## Wat is een relatie, equivalentierelatie en equivalentieklasse? Toon aan dat twee verschillende equivalentieklassen disjunct zijn.
## Geef de definitie van een relatie, equivalentieklassen en een partitie. Toon aan dat alle equivalentierelaties partities zijn.
## Wat is een functie en een injectieve functie (in symbolen)? Neem $f$, $g$ injectief, bewijs dat $f \circ g$ injectief is of geef een tegenvoorbeeld als dit niet altijd zo is.

# H3: Bewijstechnieken
## (3x) Bewijs via inductie het Binomium van Newton.
Voor $n \in \mathbb{N}$ en $x, y \in \mathbb{R}$ geldt:
$$
(x + y)^n = \sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k}.
$$

**Bewijs:**
We bewijzen via inductie naam $n$. Voor $n = 0$ klopt de stelling overduidelijk ($LR = 1 = LL$). 
Veronderstel nu dat stelling bewezen tot en met $n$. We kijken nu naar de formule voor $n + 1$:

$$
\begin{aligned}
(x + y)^{n+1} &= (x + y)^n (x + y)\\
&= \left(\sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k} \right)(x + y)\\
&= \sum_{k=0}^{n} \binom{n}{k} x^{k+1} y^{n-k} + \sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k+1}\\
&= \sum_{l=1}^{n+1} \binom{n}{l-1} x^{l} y^{n-l+1} + \sum_{k=1}^{n} \binom{n}{k} x^{k} y^{n-k+1} + \binom{n}{0}y^{n+1}\\
&= \binom{n}{n} x^{n+1} y^{0} + \sum_{l=1}^{n} \binom{n}{l-1} x^{l} y^{n-l+1} + \sum_{k=1}^{n} \binom{n}{k} x^{k} y^{n-k+1} + \binom{n}{0}y^{n+1}\\
&= \binom{n+1}{n+1} x^{n+1} + \sum_{l=1}^{n} \left[\binom{n}{l-1} + \binom{n}{l}\right] x^{l} y^{n-l+1} + \binom{n+1}{0}y^{n+1}\\
&= \binom{n+1}{n+1} x^{n+1} + \sum_{l=1}^{n} \binom{n+1}{l} x^{l} y^{n-l+1} + \binom{n+1}{0}y^{n+1}\\
&= \sum_{l=0}^{n+1} \binom{n+1}{l} x^{l} y^{n+1-l}.
\end{aligned}
$$
$\square$

## Wat is inductie? Geef alle verschillende soorten inductie. Bewijs via inductie: $\sum_{i=0}^n k^2 = \frac{n(n+1)(2n+1)}{6}$.
### Wat is inductie?

Inductie is een wiskundige techniek om stellingen te bewijzen die gelden voor een oneindige reeks objecten, vaak genummerd door natuurlijke getallen. Het idee is om te bewijzen dat een eigenschap geldt voor een basisgeval (zoals $n = 0$ of $n = 1$) en dat, als het geldt voor een willekeurige waarde $n = k$, het ook geldt voor $n = k+1$.

### Soorten inductie:
1. **Directe inductie**:
   - Hierbij worden eigendommen bewezen van natuurlijke getallen, vaak met een eenvoudige stapsgewijze redenering.
   - **Stappen**:
     - Basisgeval: Toon dat de eigenschap geldt voor $n = 0$ of $n = 1$.
     - Inductiestap: Ga ervan uit dat de eigenschap geldt voor $n = k$ (inductiehypothese) en bewijs dat het ook geldt voor $n = k+1$.
  
2. **Inductie op een structuur**:
   - Deze vorm van inductie wordt gebruikt op objecten die zijn opgebouwd uit kleinere substructuren, zoals bomen of grafen.
   - Het idee is om te bewijzen dat de eigenschap geldt voor de "basisstructuren" en dat het behoudt als een grotere structuur wordt opgebouwd uit kleinere met de inductiehypothese.

### Bewijs via directe inductie:
Bewijs dat:

$$
\sum_{i=0}^n i^2 = \frac{n(n+1)(2n+1)}{6}.
$$

#### **Stap 1: Basisgeval ($n = 0$)**
Als $n = 0$, dan is de som $\sum_{i=0}^0 i^2 = 0^2 = 0$.

Aan de rechterkant van de vergelijking:
$$
\frac{0(0+1)(2\cdot 0 + 1)}{6} = \frac{0 \cdot 1 \cdot 1}{6} = 0.
$$

Het basisgeval klopt.

#### **Stap 2: Inductiestap**
Veronderstel dat de stelling geldt voor een willekeurige $n = k$. Dat wil zeggen:
$$
\sum_{i=0}^k i^2 = \frac{k(k+1)(2k+1)}{6}.
$$

We moeten bewijzen dat de stelling ook geldt voor $n = k+1$, dus:
$$
\sum_{i=0}^{k+1} i^2 = \frac{(k+1)(k+2)(2(k+1)+1)}{6}.
$$

**Berekening**:

De som tot $k+1$ kunnen we splitsen:
$$
\sum_{i=0}^{k+1} i^2 = \sum_{i=0}^k i^2 + (k+1)^2.
$$

Vervang de inductiehypothese:
$$
\sum_{i=0}^{k+1} i^2 = \frac{k(k+1)(2k+1)}{6} + (k+1)^2.
$$

Neem $(k+1)^2$ in de berekening op:
$$
\sum_{i=0}^{k+1} i^2 = \frac{k(k+1)(2k+1)}{6} + \frac{6(k+1)^2}{6}.
$$

Factoriseer $(k+1)$ uit beide termen:
$$
\sum_{i=0}^{k+1} i^2 = \frac{(k+1) \left[ k(2k+1) + 6(k+1) \right]}{6}.
$$

Werk de termen binnen de haakjes uit:
$$
k(2k+1) + 6(k+1) = 2k^2 + k + 6k + 6 = 2k^2 + 7k + 6.
$$

Factoriseer $2k^2 + 7k + 6$:
$$
2k^2 + 7k + 6 = (k+2)(2k+3).
$$

Dus:
$$
\sum_{i=0}^{k+1} i^2 = \frac{(k+1)(k+2)(2k+3)}{6}.
$$

Dit is precies de vorm van de oorspronkelijke stelling, maar nu voor $n = k+1$.

#### **Conclusie**:
Met de basisstap en de inductiestap is bewezen dat:
$$
\sum_{i=0}^n i^2 = \frac{n(n+1)(2n+1)}{6},
$$
voor alle $n \geq 0$.

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