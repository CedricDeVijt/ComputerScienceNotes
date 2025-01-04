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

## (2x) Wat is een functie en een injectieve functie (in symbolen)? Neem $f$, $g$ injectief, bewijs dat $f \circ g$ injectief is of geef een tegenvoorbeeld als dit niet altijd zo is.

### Definitie van een functie en een injectieve functie in symbolen

1. **Functie**: Een functie $f$ van een verzameling $A$ naar een verzameling $B$ is een relatie waarbij elk element van $A$ precies één beeld heeft in $B$. Dit wordt genoteerd als:

   $$
   f: A \to B, \quad \text{met } \forall a \in A, \, \exists! b \in B \text{ zodat } f(a) = b.
   $$

2. **Injectieve functie**: Een functie $f: A \to B$ is injectief (of één-op-één) als verschillende elementen in $A$ verschillende beelden in $B$ hebben. Symbolisch:
   $$
   f \text{ is injectief} \iff \forall a_1, a_2 \in A, \, f(a_1) = f(a_2) \implies a_1 = a_2.
   $$

### Stelling: Samenstelling van injectieve functies

#### Bewering:

Als $f$ en $g$ injectieve functies zijn, dan is de samenstelling $f \circ g$ ook injectief.

#### Bewijs:

1. Laat $g: A \to B$ en $f: B \to C$ injectief zijn.
2. Beschouw $f \circ g: A \to C$, gedefinieerd door $(f \circ g)(x) = f(g(x))$ voor alle $x \in A$.
3. Om te bewijzen dat $f \circ g$ injectief is, moeten we aantonen:
   $$
   \forall x_1, x_2 \in A, \, (f \circ g)(x_1) = (f \circ g)(x_2) \implies x_1 = x_2.
   $$
4. Stel dat $(f \circ g)(x_1) = (f \circ g)(x_2)$. Dan geldt:
   $$
   f(g(x_1)) = f(g(x_2)).
   $$
5. Omdat $f$ injectief is, volgt hieruit dat:
   $$
   g(x_1) = g(x_2).
   $$
6. Omdat $g$ injectief is, volgt hieruit dat:
   $$
   x_1 = x_2.
   $$
7. Dus is $f \circ g$ injectief.

#### Conclusie:

De samenstelling van twee injectieve functies is altijd injectief.

## Wat is een partieel geordende verzameling? Wat is reflexief, anti-symmetrisch, transitief (symbolisch), stel een gegeven verzameling, toon aan dat deze reflexief, anti-symmetrisch en of transitief is. Is dit een totale orde?

Een **partieel geordende verzameling** (of poset, _partially ordered set_) is een verzameling $P$ samen met een binaire relatie $\leq$ die voldoet aan de volgende eigenschappen:

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

## Wat is minimum en minimaal element? Stel $v = 2^x$ en $x = {a, b, c}$: Bewijs dat dit een partiële ordening is.

### Minima en minimaal element

1. **Minimum (of kleinste element)**: $a \in Y$ is minimum $\iff \forall y \in Y : a \leq y$
2. **Minimaal element**: $a \in Y$ is minimaal elemenent $\iff \forall y \in Y : y \leq a \Rightarrow a = y$

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

## Wat is een relatie, equivalentierelatie en equivalentieklasse? Toon aan dat twee verschillende equivalentieklassen disjunct zijn.

### Relatie

Een **relatie** is een verzameling koppels $(a, b)$ waarin $a$ en $b$ elementen zijn van een verzameling $A$. De relatie kan een bepaalde eigenschap of verbinding tussen deze elementen beschrijven.

### Equivalentierelatie

Een **equivalentierelatie** op een verzameling $A$ is een relatie $\sim$ die voldoet aan de volgende eigenschappen:

1. **Reflexiviteit:** Voor alle $a \in A$ geldt $a \sim a$.
2. **Symmetrie:** Voor alle $a, b \in A$, als $a \sim b$, dan $b \sim a$.
3. **Transitiviteit:** Voor alle $a, b, c \in A$, als $a \sim b$ en $b \sim c$, dan $a \sim c$.

### Equivalentieklasse

Een **equivalentieklasse** van een element $a \in A$ onder een equivalentierelatie $\sim$ is de verzameling van alle elementen in $A$ die equivalent zijn aan $a$:

$$
[a] = \{x \in A \mid x \sim a\}.
$$

Equivalentieklassen delen de verzameling $A$ op in disjuncte deelverzamelingen, waarbij elk element van $A$ in precies één equivalentieklasse zit.

### Twee verschillende equivalentieklassen zijn disjunct

**Bewering:** Als $[a]$ en $[b]$ twee verschillende equivalentieklassen zijn onder een equivalentierelatie $\sim$, dan geldt:

$$
[a] \cap [b] = \emptyset \quad \text{(disjunctie)}.
$$

#### Bewijs:

1. Stel dat $[a] \cap [b] \neq \emptyset$. Dit betekent dat er een element $x$ is dat in beide klassen zit, dus:
   $$
   x \in [a] \quad \text{en} \quad x \in [b].
   $$
2. Omdat $x \in [a]$, geldt volgens de definitie van een equivalentieklasse:
   $$
   x \sim a.
   $$
3. Omdat $x \in [b]$, geldt ook:
   $$
   x \sim b.
   $$
4. Omdat $\sim$ een equivalentierelatie is en dus transitief, volgt hieruit:
   $$
   a \sim b.
   $$
5. Als $a \sim b$, dan is $[a] = [b]$, want alle elementen die equivalent zijn aan $a$ zijn ook equivalent aan $b$, en vice versa.
6. Dit is in tegenspraak met de aanname dat $[a]$ en $[b]$ verschillend zijn.

#### Conclusie:

Als $[a] \neq [b]$, dan is $[a] \cap [b] = \emptyset$. Equivalentieklassen zijn dus disjunct.

## Geef de definitie van een relatie, equivalentieklassen en een partitie. Toon aan dat alle equivalentierelaties partities zijn.

Hier zijn de definities en de uitleg van het verband tussen equivalentierelaties en partities:

### Definitie van een relatie

Een **relatie** $R$ op een verzameling $A$ is een deelverzameling van het cartesiaanse product $A \times A$. Een paar $(a, b) \in A \times A$ behoort tot $R$ als $a$ in relatie staat tot $b$, genoteerd als $aRb$.

### Definitie van een equivalentierelatie

Een **equivalentierelatie** op een verzameling $A$ is een relatie $R \subseteq A \times A$ die voldoet aan de volgende eigenschappen:

1. **Reflexiviteit**: Voor alle $a \in A$ geldt $aRa$.
2. **Symmetrie**: Als $aRb$, dan $bRa$ (voor alle $a, b \in A$).
3. **Transitiviteit**: Als $aRb$ en $bRc$, dan $aRc$ (voor alle $a, b, c \in A$).

### Equivalentieklassen

De **equivalentieklasse** van een element $a \in A$ ten opzichte van een equivalentierelatie $R$ wordt gedefinieerd als de verzameling:

$$
[a] = \{ x \in A \mid aRx \}.
$$

Deze klasse bevat alle elementen die equivalent zijn aan $a$.

### Definitie van een partitie

Een **partitie** van een verzameling $A$ is een verzameling $\mathcal{P}$ van niet-lege deelverzamelingen van $A$, zodanig dat:

1. De deelverzamelingen in $\mathcal{P}$ elkaar niet overlappen, oftewel $X \cap Y = \emptyset$ voor $X, Y \in \mathcal{P}$ met $X \neq Y$.
2. De vereniging van de deelverzamelingen gelijk is aan $A$, oftewel $\bigcup_{X \in \mathcal{P}} X = A$.

### Bewijs: Elke equivalentierelatie bepaalt een partitie

We willen aantonen dat de equivalentieklassen van een equivalentierelatie een partitie vormen van $A$.

#### 1. Niet-lege deelverzamelingen

Voor elk $a \in A$ is de equivalentieklasse $[a]$ niet-leeg, omdat $a \in [a]$ (door reflexiviteit).

#### 2. Disjunctie van equivalentieklassen

We tonen aan dat twee verschillende equivalentieklassen $[a]$ en $[b]$ elkaar niet overlappen, oftewel $[a] \cap [b] = \emptyset$ als $[a] \neq [b]$.

- Stel dat $[a] \cap [b] \neq \emptyset$. Dan is er een $x \in [a] \cap [b]$, wat betekent dat $x \in [a]$ en $x \in [b]$.
- Omdat $x \in [a]$, geldt $aRx$. Omdat $x \in [b]$, geldt $bRx$. Door symmetrie en transitiviteit volgt $aRb$.
- Als $aRb$, zijn $[a]$ en $[b]$ identiek. Dit is in tegenspraak met de aanname dat $[a] \neq [b]$. Dus $[a] \cap [b] = \emptyset$.

#### 3. Vereniging van alle equivalentieklassen

De vereniging van alle equivalentieklassen is gelijk aan $A$. Elk element $a \in A$ behoort per definitie tot zijn eigen equivalentieklasse $[a]$, en dus is $A = \bigcup_{a \in A} [a]$.

**Conclusie:** De equivalentieklassen van een equivalentierelatie vormen een partitie van $A$.

# H3: Bewijstechnieken

## (3x) Bewijs via inductie het Binomium van Newton.

Voor $n \in \mathbb{N}$ en $x, y \in \mathbb{R}$ geldt:

$$
(x + y)^n = \sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k}.
$$

### Bewijs:

We zullen dit bewijzen via inductie over $n$.

#### **Basisgeval ($n = 0$)**:

Voor $n = 0$ is de bewering:

$$
(x + y)^0 = 1 = \binom{0}{0} x^0 y^0.
$$

Dit klopt, want $1 = 1$.

#### **Inductiehypothese**:

Veronderstel dat de bewering waar is voor $n = k$, dus:

$$
(x + y)^k = \sum_{l=0}^{k} \binom{k}{l} x^{l} y^{k-l}.
$$

#### **Inductiestap**:

We moeten bewijzen dat de bewering ook waar is voor $n = k+1$, dus:

$$
\begin{aligned}
(x + y)^{n+1} &= (x + y)^n (x + y)\\
&= \left(\sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k} \right)(x + y)\\
&= \sum_{k=0}^{n} \binom{n}{k} x^{k+1} y^{n-k} + \sum_{k=0}^{n} \binom{n}{k} x^{k} y^{n-k+1}\\
&= \sum_{l=1}^{n+1} \binom{n}{l-1} x^{l} y^{n-l+1} + \sum_{k=1}^{n} \binom{n}{k} x^{k} y^{n-k+1} + \binom{n}{0}y^{n+1}\\
&= \binom{n}{n} x^{n+1} y^{0} + \sum_{l=1}^{n} \binom{n}{l-1} x^{l} y^{n-l+1} + \sum_{k=1}^{n} \binom{n}{k} x^{k} y^{n-k+1} + \binom{n}{0}y^{n+1}\\
&= \binom{n+1}{n+1} x^{n+1} + \sum_{l=1}^{n} \left[\binom{n}{l-1} + \binom{n}{l}\right] x^{l} y^{n-l+1} + \binom{n+1}{0}y^{n+1}\\
&= \binom{n+1}{n+1} x^{n+1} + \sum_{l=1}^{n} \binom{n+1}{l} x^{l} y^{n-l+1} + \binom{n+1}{0}y^{n+1}\\
&= \sum_{l=0}^{n+1} \binom{n+1}{l} x^{l} y^{n+1-l}
\end{aligned}
$$

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

\

# H5: Kansrekening

## Wat is een poisson verdeling (symbolisch)? Leid de verwachtingswaarde af. Wat is een toevalsveranderlijke. Bewijs $E(x+y) = ?$. Bewijs voor hetzelfde ook de var.

Een **Poisson-verdeling** beschrijft de kans op een bepaald aantal gebeurtenissen in een vaste tijdsperiode of ruimte, onder de aanname dat de gebeurtenissen onafhankelijk zijn en met een constante gemiddelde snelheid plaatsvinden. Symbolisch wordt een Poisson-verdeling gegeven door:

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \ldots
$$

waar:

- $X$ de toevalsvariabele is die het aantal gebeurtenissen weergeeft,
- $\lambda > 0$ de verwachtingswaarde én variantie is (het gemiddelde aantal gebeurtenissen),
- $k!$ de faculteit van $k$.

### **Wat is een toevalsvariabele?**

Een **toevalsvariabele** is een wiskundige functie die uitkomsten van een kansexperiment aan numerieke waarden koppelt. Bijvoorbeeld:

- Bij het gooien van een munt: $X = 1$ als kop en $X = 0$ als munt.
- Bij een Poisson-verdeling: $X$ is het aantal gebeurtenissen in een gegeven interval.

Toevalsvariabelen kunnen discreet (bijv. $X = 0, 1, 2, \ldots$) of continu zijn (bijv. $X \in \mathbb{R}$).

### **Leid de verwachtingswaarde van de Poisson-verdeling af**

De verwachtingswaarde $E[X]$ van een Poisson-verdeling wordt berekend als:

$$
E[X] = \sum_{k=0}^\infty k \cdot P(X = k) = \sum_{k=0}^\infty k \cdot \frac{\lambda^k e^{-\lambda}}{k!}.
$$

We herschrijven $k$ als $k = m+1$, zodat $k! = (m+1)! = (m+1)m!$. Daarmee:

$$
E[X] = \sum_{k=1}^\infty k \cdot \frac{\lambda^k e^{-\lambda}}{k!} = \sum_{m=0}^\infty (m+1) \cdot \frac{\lambda^{m+1} e^{-\lambda}}{(m+1)!}.
$$

Vereenvoudig:

$$
E[X] = \sum_{m=0}^\infty \lambda \cdot \frac{\lambda^m e^{-\lambda}}{m!}.
$$

De som van $\sum_{m=0}^\infty \frac{\lambda^m e^{-\lambda}}{m!}$ is precies 1 (de som van de kansen van een Poisson-verdeling). Dus:

$$
E[X] = \lambda.
$$

### **Bewijs $E[X+Y] = E[X] + E[Y]$**

Voor twee toevalsvariabelen $X$ en $Y$, geldt:

$$
E[X+Y] = \sum_{x, y} (x+y) P(X=x, Y=y).
$$

Omdat $P(X=x, Y=y)$ de gezamenlijke kansverdeling is, herschrijf je:

$$
E[X+Y] = \sum_{x, y} x \cdot P(X=x, Y=y) + \sum_{x, y} y \cdot P(X=x, Y=y).
$$

De eerste term geeft $E[X]$, en de tweede geeft $E[Y]$. Dus:

$$
E[X+Y] = E[X] + E[Y].
$$

Dit geldt ook als $X$ en $Y$ afhankelijk zijn.

### **Bewijs $\text{Var}(X+Y)$:**

De variantie van een som $X+Y$ wordt gegeven door:

$$
\text{Var}(X+Y) = E[(X+Y)^2] - (E[X+Y])^2.
$$

Uitwerken:

$$
E[(X+Y)^2] = E[X^2] + 2E[XY] + E[Y^2],
$$

$$
(E[X+Y])^2 = (E[X] + E[Y])^2 = E[X]^2 + 2E[X]E[Y] + E[Y]^2.
$$

Hieruit volgt:

$$
\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y) + 2(\text{Cov}(X, Y)),
$$

waarbij $\text{Cov}(X, Y) = E[XY] - E[X]E[Y]$. Als $X$ en $Y$ onafhankelijk zijn, geldt $\text{Cov}(X, Y) = 0$, en dan:

$$
\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y).
$$

## Wat is een poissonverdeelde toevalsveranderlijke? Wat is de variantie ervan? Bewijs.

Een **Poissonverdeelde toevalsvariabele** wordt gebruikt om het aantal gebeurtenissen te modelleren dat plaatsvindt in een vast tijdsinterval of gebied, onder de volgende voorwaarden:

1. **Gebeurtenissen vinden onafhankelijk plaats**: De kans op een gebeurtenis in een bepaald interval is onafhankelijk van gebeurtenissen in andere intervallen.
2. **Constante gemiddelde snelheid ($\lambda$)**: Het gemiddelde aantal gebeurtenissen in een gegeven interval is constant.
3. **Geen gelijktijdige gebeurtenissen**: De kans op meer dan één gebeurtenis in een zeer klein interval is verwaarloosbaar.

De kansverdelingsfunctie van een Poissonverdeelde toevalsvariabele $X$ wordt gegeven door:

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \ldots
$$

Hierbij is:

- $\lambda > 0$: het verwachte aantal gebeurtenissen in het interval (de parameter van de verdeling),
- $k$: het waargenomen aantal gebeurtenissen.

### **Verwachtingswaarde en variantie van een Poissonverdeelde variabele**

#### Verwachtingswaarde ($E[X]$)

Voor een Poissonverdeelde toevalsvariabele is de verwachtingswaarde gelijk aan $\lambda$. Dit kan als volgt worden bewezen:

$$
E[X] = \sum_{k=0}^\infty k \cdot P(X = k) = \sum_{k=0}^\infty k \cdot \frac{\lambda^k e^{-\lambda}}{k!}.
$$

Door herschikking en verschuiving in de som:

1. Haal $e^{-\lambda}$ en $\lambda$ buiten de som:
   $$
   E[X] = \lambda e^{-\lambda} \sum_{k=1}^\infty \frac{\lambda^{k-1}}{(k-1)!}.
   $$
2. Laat $j = k-1$, waardoor $k = j+1$:
   $$
   E[X] = \lambda e^{-\lambda} \sum_{j=0}^\infty \frac{\lambda^j}{j!}.
   $$
3. Merk op dat de som $\sum_{j=0}^\infty \frac{\lambda^j}{j!} = e^\lambda$ (de Taylorreeks van $e^\lambda$):
   $$
   E[X] = \lambda \cdot e^{-\lambda} \cdot e^\lambda = \lambda.
   $$

#### Variantie ($\text{Var}(X)$)

Voor een Poissonverdeelde toevalsvariabele geldt dat de variantie gelijk is aan de verwachtingswaarde, dus $\text{Var}(X) = \lambda$.

Dit kan worden bewezen met behulp van de formule voor de variantie:

$$
\text{Var}(X) = E[X^2] - (E[X])^2.
$$

##### Berekening van $E[X^2]$:

$$
E[X^2] = \sum_{k=0}^\infty k^2 \cdot P(X = k) = \sum_{k=0}^\infty k^2 \cdot \frac{\lambda^k e^{-\lambda}}{k!}.
$$

Splits $k^2$ op als $k(k-1) + k$:

$$
E[X^2] = \sum_{k=0}^\infty k(k-1) \cdot \frac{\lambda^k e^{-\lambda}}{k!} + \sum_{k=0}^\infty k \cdot \frac{\lambda^k e^{-\lambda}}{k!}.
$$

- Voor de eerste term ($k(k-1)$):
  Laat $j = k-2$, zodat $k(k-1) = \lambda^2 e^{-\lambda} \sum_{j=0}^\infty \frac{\lambda^j}{j!} = \lambda^2$.

- Voor de tweede term ($k$):
  Dit is gelijk aan $E[X] = \lambda$.

Samen:

$$
E[X^2] = \lambda^2 + \lambda.
$$

##### Berekening van de variantie:

$$
\text{Var}(X) = E[X^2] - (E[X])^2 = (\lambda^2 + \lambda) - \lambda^2 = \lambda.
$$

### Conclusie

Een Poissonverdeelde toevalsvariabele heeft:

- **Verwachtingswaarde**: $E[X] = \lambda$,
- **Variantie**: $\text{Var}(X) = \lambda$.

## Wat is een normaalverdeelde toevalsveranderlijke? Hoe en wanneer kunnen we hier een binomiale verdeling mee benaderen?

Een **normaalverdeelde toevalsvariabele** is een variabele die wordt gekarakteriseerd door een normale verdeling, een bekende kansverdeling met een klokvormige symmetrie. De verdeling wordt volledig beschreven door twee parameters:

1. **Het gemiddelde** ($\mu$): Dit is het centrum van de verdeling en geeft de verwachte waarde van de toevalsvariabele aan.
2. **De standaardafwijking** ($\sigma$): Dit meet de spreiding van de verdeling. Hoe groter $\sigma$, hoe breder de verdeling.

De kansdichtheidsfunctie van een normaalverdeelde variabele $X \sim N(\mu, \sigma^2)$ wordt gegeven door:

$$
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}}
$$

### Wanneer een binomiale verdeling benaderen met een normale verdeling?

Een binomiale verdeling wordt gebruikt om het aantal successen in $n$ onafhankelijke Bernoulli-experimenten te modelleren, waarbij de kans op succes in elk experiment gelijk is aan $p$. De parameters van een binomiale verdeling zijn $n$ (het aantal experimenten) en $p$ (de succeskans).

In sommige situaties kun je een binomiale verdeling benaderen met een normale verdeling:

#### Voorwaarden voor de benadering:

1. **Grote $n$:** Het aantal experimenten moet groot genoeg zijn.
2. **Niet te kleine $p$ of $1-p$:** De kansen $np \geq 5$ en $n(1-p) \geq 5$ moeten voldoen. Dit zorgt ervoor dat de binomiale verdeling symmetrisch genoeg is.

#### Hoe werkt de benadering?

De binomiale verdeling $B(n, p)$ kan worden benaderd door een normale verdeling $N(\mu, \sigma^2)$ met:

- **Gemiddelde:** $\mu = np$
- **Variantie:** $\sigma^2 = np(1-p)$
- **Standaardafwijking:** $\sigma = \sqrt{np(1-p)}$

#### Continuïteitscorrectie:

Omdat een binomiale verdeling discreet is (alleen gehele waarden), en een normale verdeling continu, moet je vaak een continuïteitscorrectie toepassen. Dit houdt in dat je 0,5 optelt of aftrekt van de grenzen van de intervallen bij het berekenen van kansen. Bijvoorbeeld:

- De kans dat $X = k$ in een binomiale verdeling wordt benaderd door de kans dat $k - 0,5 \leq X \leq k + 0,5$ in een normale verdeling.

#### Voorbeeld:

Een munt wordt 100 keer gegooid ($n = 100$), en de kans op kop is $p = 0,5$. Dan geldt:

- $\mu = np = 100 \cdot 0,5 = 50$
- $\sigma = \sqrt{np(1-p)} = \sqrt{100 \cdot 0,5 \cdot 0,5} = 5$

De binomiale verdeling $B(100, 0,5)$ kan worden benaderd door de normale verdeling $N(50, 5^2)$.

Als je de kans wilt berekenen dat $X \leq 45$, gebruik je de continuïteitscorrectie:

$$
P(X \leq 45) \approx P(Y \leq 45{,}5), \quad Y \sim N(50, 5^2)
$$

Deze benadering wordt vaak gebruikt omdat het rekenen met een normale verdeling eenvoudiger is dan met een binomiale verdeling, vooral bij grote $n$.

## Wat is de formule voor de variantie van een binomiale verdeling? Bewijs.

De **variantie van een binomiale verdeling** met parameters $n$ (aantal onafhankelijke proeven) en $p$ (kans op succes bij een enkele proef) wordt gegeven door de formule:

$$
\text{Var}(X) = n \cdot p \cdot (1-p),
$$

waarbij $X \sim \text{Bin}(n, p)$. Hieronder volgt een bewijs van deze formule:

### Bewijs:

**1. Verwachtingswaarde en variantie van een bernoilliproef**

Bij een enkele Bernoulli-proef met kans op succes $p$, is de uitkomst $X_i$ gelijk aan 1 (succes) of 0 (falen).

- Verwachtingswaarde:

  $$
  \mathbb{E}[X_i] = p.
  $$

- Variantie:
  $$
  \text{Var}(X_i) = \mathbb{E}[X_i^2] - (\mathbb{E}[X_i])^2.
  $$
  Omdat $X_i^2 = X_i$ (bij 0 of 1 blijft het kwadraat gelijk), geldt:
  $$
  \mathbb{E}[X_i^2] = \mathbb{E}[X_i] = p.
  $$
  Dus:
  $$
  \text{Var}(X_i) = p - p^2 = p(1-p).
  $$

**2. Som van onafhankelijke Bernoulli-proeven**

Een binomiale verdeling is de som van $n$ onafhankelijke Bernoulli-proeven:

$$
X = \sum_{i=1}^n X_i,
$$

waarbij elk $X_i \sim \text{Bernoulli}(p)$.

- Verwachtingswaarde:
  Door de lineariteit van de verwachting:

  $$
  \mathbb{E}[X] = \mathbb{E}\left[\sum_{i=1}^n X_i\right] = \sum_{i=1}^n \mathbb{E}[X_i] = n \cdot p.
  $$

- Variantie:
  Omdat de $X_i$ onafhankelijk zijn, geldt dat de variantie van de som gelijk is aan de som van de varianties:
  $$
  \text{Var}(X) = \text{Var}\left(\sum_{i=1}^n X_i\right) = \sum_{i=1}^n \text{Var}(X_i).
  $$
  Omdat $\text{Var}(X_i) = p(1-p)$ voor elke $i$, volgt:
  $$
  \text{Var}(X) = \sum_{i=1}^n p(1-p) = n \cdot p \cdot (1-p).
  $$

**Conclusie:**
De variantie van een binomiale verdeling is:

$$
\text{Var}(X) = n \cdot p \cdot (1-p).
$$

## Bewijs $E[x+y]$ en $var(x+y)$ en geef de voorwaarde hiervoor.

We bewijzen hier de eigenschappen van de verwachtingswaarde ($E$) en variantie ($\text{var}$) voor de som van twee willekeurige stochastische variabelen $X$ en $Y$.

### Bewijs van $E[X + Y] = E[X] + E[Y]$

De eigenschap geldt zonder aanvullende voorwaarden en volgt uit de lineariteit van de verwachtingswaarde.

1. **Definitie van $E[X+Y]$:**

   $$
   E[X + Y] = \int*{-\infty}^{\infty} \int*{-\infty}^{\infty} (x + y) f*{X,Y}(x, y) \, dx \, dy
   $$

   waarbij $f*{X,Y}(x, y)$ de gezamenlijke kansdichtheid van $X$ en $Y$ is.

2. **Splits de som binnen de integratie:**

   $$
   E[X + Y] = \int*{-\infty}^{\infty} \int*{-\infty}^{\infty} x f*{X,Y}(x, y) \, dx \, dy + \int*{-\infty}^{\infty} \int*{-\infty}^{\infty} y f*{X,Y}(x, y) \, dx \, dy
   $$

3. **Integreer over de marginale verdelingen:**
   De eerste term wordt:

   $$
   \int*{-\infty}^{\infty} x \left( \int*{-\infty}^{\infty} f*{X,Y}(x, y) \, dy \right) dx = \int*{-\infty}^{\infty} x f*X(x) \, dx = E[X]
   $$

   (waarbij $f_X(x) = \int*{-\infty}^\infty f\_{X,Y}(x, y) \, dy$). Een soortgelijke afleiding geldt voor de tweede term, die $E[Y]$ oplevert.

4. **Conclusie:**
   $$
   E[X + Y] = E[X] + E[Y].
   $$

### Bewijs van $\text{var}(X + Y)$

De formule voor $\text{var}(X+Y)$ is:

$$
\text{var}(X + Y) = \text{var}(X) + \text{var}(Y) + 2\text{cov}(X, Y),
$$

waarbij $\text{cov}(X, Y) = E[(X - E[X])(Y - E[Y])]$.

#### Bewijs

1. **Definitie van de variantie:**

   $$
   \text{var}(X+Y) = E[(X+Y)^2] - \left(E[X+Y]\right)^2.
   $$

2. **Bereken $E[(X+Y)^2]$:**
   Uitwerken van $(X+Y)^2$ geeft:

   $$
   E[(X+Y)^2] = E[X^2 + 2XY + Y^2].
   $$

   Gebruik lineariteit van de verwachtingswaarde:

   $$
   E[(X+Y)^2] = E[X^2] + 2E[XY] + E[Y^2].
   $$

3. **Bereken $\left(E[X+Y]\right)^2$:**
   Uit de lineariteit volgt:

   $$
   \left(E[X+Y]\right)^2 = \left(E[X] + E[Y]\right)^2 = E[X]^2 + 2E[X]E[Y] + E[Y]^2.
   $$

4. **Substitueer in de definitie van de variantie:**

   $$
   \text{var}(X+Y) = E[X^2] + 2E[XY] + E[Y^2] - \left(E[X]^2 + 2E[X]E[Y] + E[Y]^2\right).
   $$

5. **Herschat termen:**
   Gebruik de definitie van de variantie ($\text{var}(X) = E[X^2] - E[X]^2$) en covariantie ($\text{cov}(X, Y) = E[XY] - E[X]E[Y]$):
   $$
   \text{var}(X+Y) = \text{var}(X) + \text{var}(Y) + 2\text{cov}(X, Y).
   $$

### Voorwaarden

- Voor $E[X + Y] = E[X] + E[Y]$: **Geen aanvullende voorwaarden nodig.** Deze eigenschap geldt altijd.
- Voor $\text{var}(X + Y)$: De variantieformule is afhankelijk van de **covariantie**. Bij onafhankelijkheid van $X$ en $Y$ geldt $\text{cov}(X, Y) = 0$, en dan:
  $$
  \text{var}(X+Y) = \text{var}(X) + \text{var}(Y).
  $$

## Wat is een toevalsveranderlijke? Toon aan dat de som van $X$ ~ $NB(n, p)$: $P(X_i) = 1$.

Een **toevalsveranderlijke** (of stochastische variabele) is een functie die aan elke mogelijke uitkomst van een kansruimte een numerieke waarde toekent. Deze variabelen worden gebruikt in kansrekening om stochastische processen en onzekerheden te modelleren. Toevalsveranderlijken kunnen discreet (zoals een dobbelsteenworp) of continu (zoals de tijd tot een gebeurtenis) zijn.

### Negatief-binomiale verdeling (NB)

De **negatief-binomiale verdeling** $NB(n, p)$ beschrijft het aantal mislukkingen ($X$) vóórdat $n$ successen optreden in een reeks onafhankelijke Bernoulli-experimenten met succeskans $p$.

De kansfunctie van $X \sim NB(n, p)$ wordt gegeven door:

$$
P(X = k) = \binom{n+k-1}{k} p^n (1-p)^k, \quad k = 0, 1, 2, \ldots
$$

### Bewijs dat $\sum\_{X} P(X) = 1$

We willen aantonen dat de kansen van alle mogelijke uitkomsten $X$ optellen tot 1, wat een noodzakelijke eigenschap is van elke kansverdeling.

#### Uitwerking

De som over alle mogelijke waarden van $X$ is:

$$
\sum*{k=0}^\infty P(X = k) = \sum*{k=0}^\infty \binom{n+k-1}{k} p^n (1-p)^k.
$$

De binomiaalcoëfficiënt kan herschreven worden als:

$$
\binom{n+k-1}{k} = \frac{(n+k-1)!}{k!(n-1)!}.
$$

Nu substitueren we dit terug in de som:

$$
\sum*{k=0}^\infty P(X = k) = p^n \sum*{k=0}^\infty \frac{(n+k-1)!}{k!(n-1)!} (1-p)^k.
$$

We herkennen hier een bekende eigenschap van de negatieve binomiale reeks. Voor $|1-p| < 1$ geldt:

$$
\sum\_{k=0}^\infty \binom{n+k-1}{k} (1-p)^k = \frac{1}{p^n}.
$$

Hieruit volgt:

$$
\sum\_{k=0}^\infty P(X = k) = p^n \cdot \frac{1}{p^n} = 1.
$$

### Conclusie

De som van alle kansen van een negatief-binomiale verdeling is gelijk aan 1, wat bevestigt dat het een geldige kansverdeling is.

## Leg de paradox van Simpson uit met een voorbeeld.

### De paradox van Simpson uitgelegd met een voorbeeld

De paradox van Simpson (ook wel het Simpson-effect genoemd) is een statistisch fenomeen waarbij een trend die zichtbaar is in meerdere groepen verdwijnt of omkeert wanneer de groepen worden samengevoegd. Het toont aan hoe belangrijk het is om gegevens in context te bekijken en niet alleen op algemene trends te vertrouwen.

### Voorbeeld: Medische behandeling

Stel je voor dat we een studie doen naar de effectiviteit van twee behandelingen voor een bepaalde ziekte: **Behandeling A** en **Behandeling B**. De gegevens worden geanalyseerd voor mannen en vrouwen afzonderlijk, en vervolgens gecombineerd.

#### Gegevens per geslacht

| Geslacht | Behandeling A (succes) | Behandeling A (totaal) | Behandeling B (succes) | Behandeling B (totaal) |
| -------- | ---------------------- | ---------------------- | ---------------------- | ---------------------- |
| Mannen   | 90/100 (90%)           | 90/100                 | 60/80 (75%)            | 60/80                  |
| Vrouwen  | 30/50 (60%)            | 30/50                  | 30/40 (75%)            | 30/40                  |

**Analyse per geslacht:**

- Bij mannen is Behandeling A effectiever (90% vs. 75%).
- Bij vrouwen is Behandeling B effectiever (75% vs. 60%).

#### Gecombineerde gegevens

Als we de gegevens samenvoegen zonder onderscheid naar geslacht:

| Behandeling | Succes | Totaal | Succespercentage |
| ----------- | ------ | ------ | ---------------- |
| A           | 120    | 150    | 80%              |
| B           | 90     | 120    | 75%              |

**Gecombineerde analyse:**

- Nu lijkt Behandeling A effectiever (80% vs. 75%).

### Wat gebeurt er hier?

De paradox ontstaat door het verschil in verdeling van mannen en vrouwen tussen de behandelingen:

- Behandeling A werd vaker toegepast bij mannen (die een hoger succespercentage hebben).
- Behandeling B werd vaker toegepast bij vrouwen (die ook een hoger succespercentage hebben).

Dit vertekent het gecombineerde succespercentage en creëert een schijnbare trend die in de afzonderlijke groepen niet zichtbaar is.

### Belangrijke lessen

1. **Context is cruciaal:** Analyseer data op verschillende niveaus (zoals subgroepen) voordat je conclusies trekt.
2. **Verstoorders identificeren:** Demografische of andere factoren kunnen resultaten beïnvloeden.
3. **Causaliteit vermijden:** De paradox van Simpson laat zien dat correlaties misleidend kunnen zijn zonder de juiste context.

Dit voorbeeld benadrukt hoe je voorzichtig moet zijn met statistische interpretaties!

## Wat is een binomiaal verdeelde toevalsveranderlijke? Bewijs E(x).

Een **binomiaal verdeelde toevalsveranderlijke** is een type discrete kansverdeling die wordt gebruikt om het aantal successen te modelleren in een vaste reeks van $n$ onafhankelijke Bernoulli-experimenten, waarbij elk experiment twee mogelijke uitkomsten heeft: succes (met kans $p$) of mislukking (met kans $1-p$).

Als $X$ een binomiaal verdeelde toevalsveranderlijke is, dan schrijven we:

$$
X \sim \text{Bin}(n, p),
$$

waarbij:

- $n$: het aantal experimenten,
- $p$: de kans op succes per experiment.

De kansfunctie wordt gegeven door:

$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \dots, n,
$$

waarbij $\binom{n}{k} = \frac{n!}{k!(n-k)!}$ het aantal manieren is om $k$ successen uit $n$ experimenten te kiezen.

### Bewijs van de verwachtingswaarde $E(X)$

De verwachtingswaarde van $X$ wordt gedefinieerd als:

$$
E(X) = \sum\_{k=0}^n k \cdot P(X = k).
$$

Substitueer de kansfunctie van de binomiale verdeling:

$$
E(X) = \sum\_{k=0}^n k \cdot \binom{n}{k} p^k (1-p)^{n-k}.
$$

We herschrijven $k \cdot \binom{n}{k}$ met de eigenschap:

$$
k \cdot \binom{n}{k} = n \cdot \binom{n-1}{k-1},
$$

waardoor:

$$
E(X) = \sum\_{k=1}^n n \cdot \binom{n-1}{k-1} p^k (1-p)^{n-k}.
$$

Vervang $j = k-1$, wat betekent $k = j+1$ en de somlimieten veranderen:

$$
E(X) = n \sum\_{j=0}^{n-1} \binom{n-1}{j} p^{j+1} (1-p)^{n-1-j}.
$$

Splits $p^{j+1}$ op in $p \cdot p^j$:

$$
E(X) = n \cdot p \sum\_{j=0}^{n-1} \binom{n-1}{j} p^j (1-p)^{(n-1)-j}.
$$

De som in deze uitdrukking is de binomiale expansie van $(p + (1-p))^{n-1} = 1$:

$$
\sum\_{j=0}^{n-1} \binom{n-1}{j} p^j (1-p)^{n-1-j} = 1.
$$

Dus:

$$
E(X) = n \cdot p \cdot 1 = n \cdot p.
$$

### Resultaat

De verwachtingswaarde van een binomiaal verdeelde toevalsveranderlijke is:

$$
E(X) = n \cdot p.
$$

## Bewijs de regel van Bayes en de somregel.

De regel van Bayes en de somregel zijn fundamentele regels in de kansrekening. Hieronder wordt de wiskundige bewijsvoering van beide regels uitgewerkt.

### **De Regel van Bayes**

De regel van Bayes wordt als volgt geformuleerd:

$$
P(A \mid B) = \frac{P(B \mid A) P(A)}{P(B)} \quad \text{(mits $P(B) > 0$)}.
$$

#### **Bewijs:**

1. Volgens de definitie van voorwaardelijke kans hebben we:

   $$
   P(A \mid B) = \frac{P(A \cap B)}{P(B)} \quad \text{(mits $P(B) > 0$)}.
   $$

2. Evenzo, voor $P(B \mid A)$:

   $$
   P(B \mid A) = \frac{P(A \cap B)}{P(A)} \quad \text{(mits $P(A) > 0$)}.
   $$

3. Door de formule voor $P(B \mid A)$ om te schrijven, krijgen we:

   $$
   P(A \cap B) = P(B \mid A) P(A).
   $$

4. Substitueer $P(A \cap B)$ in de definitie van $P(A \mid B)$:
   $$
   P(A \mid B) = \frac{P(A \cap B)}{P(B)} = \frac{P(B \mid A) P(A)}{P(B)}.
   $$

Dit is de regel van Bayes.

### **De Somregel**

De somregel wordt als volgt geformuleerd:

$$
P(B) = \sum\_{i} P(B \cap A_i),
$$

waar $\{A_i\}$ een partitie van de uitkomstenruimte $\Omega$ vormt.

#### **Bewijs:**

1. Stel dat $\{A_i\}$ een partitie vormt van $\Omega$. Dit betekent dat:

   - De gebeurtenissen $A_i$ disjunct zijn ($A_i \cap A_j = \emptyset$ voor $i \neq j$).
   - De unie van alle $A_i$ de volledige uitkomstenruimte $\Omega$ beslaat ($\bigcup_i A_i = \Omega$).

2. Schrijf $B$ als een unie van doorsneden met elk deel van de partitie:

   $$
   B = \bigcup_i (B \cap A_i).
   $$

3. Omdat de $A_i$ disjunct zijn, zijn de doorsneden $B \cap A_i$ ook disjunct. Daarom geldt:
   $$
   P(B) = \sum_i P(B \cap A_i).
   $$

Dit is de somregel.

### Toepassing van de Somregel in de Regel van Bayes

In de context van de regel van Bayes wordt $P(B)$ vaak uitgedrukt via de somregel:

$$
P(B) = \sum_i P(B \cap A_i) = \sum_i P(B \mid A_i) P(A_i).
$$

Dit maakt de regel van Bayes expliciet afhankelijk van alle mogelijke $A_i$ in een partitie.

## Wat is een toevalsveranderlijke? Toon aan dat de som van $X$ ~ $NB(n, p)$: $P(X_i) = 1$.

### Wat is een toevalsveranderlijke?

Een **toevalsveranderlijke** is een functie die aan elke uitkomst van een kansexperiment een reëel getal toekent. Het is een abstracte manier om uitkomsten van een kansproces te kwantificeren en wiskundig te analyseren. Er zijn twee soorten toevalsveranderlijken:

1. **Discreet**: Hierbij neemt de toevalsveranderlijke een eindig of aftelbaar aantal waarden aan, zoals $X \in \{0, 1, 2, \dots\}$.
2. **Continu**: Hierbij neemt de toevalsveranderlijke een ononderbroken reeks waarden aan, zoals $X \in \mathbb{R}$.

De verdeling van een toevalsveranderlijke geeft de kans weer dat de toevalsveranderlijke een specifieke waarde of een reeks waarden aanneemt.

### Negatief-binomiale verdeling ($NB(n, p)$)

Een toevalsveranderlijke $X$ volgt een **negatief-binomiale verdeling**, genoteerd als $NB(n, p)$, als deze het aantal mislukkingen $X$ telt voordat de $n$-de succes wordt bereikt in een reeks van Bernoulli-proeven met succeskans $p$. De kansmassa-functie (PMF) is:

$$
P(X = k) = \binom{n + k - 1}{k} p^n (1-p)^k, \quad k = 0, 1, 2, \dots
$$

waarbij:

- $n$ het aantal successen is,
- $k$ het aantal mislukkingen,
- $p$ de kans op succes bij elke proef.

Het doel is nu aan te tonen dat de totale kans over alle mogelijke waarden van $X$ gelijk is aan 1, oftewel:

$$
\sum_{k=0}^\infty P(X = k) = 1.
$$

### Bewijs: $\sum_{k=0}^\infty P(X = k) = 1$

1. **Kansmassa-functie invoeren**:
   De kansmassa-functie voor $X \sim NB(n, p)$ is:

   $$
   P(X = k) = \binom{n + k - 1}{k} p^n (1-p)^k.
   $$

   De totale kanssom is:

   $$
   \sum_{k=0}^\infty P(X = k) = \sum_{k=0}^\infty \binom{n + k - 1}{k} p^n (1-p)^k.
   $$

2. **Schrijf de binomiaalcoëfficiënt expliciet uit**:
   De binomiaalcoëfficiënt kan herschreven worden als:

   $$
   \binom{n + k - 1}{k} = \frac{(n+k-1)!}{k! (n-1)!}.
   $$

   Substitueer dit in de som:

   $$
   \sum_{k=0}^\infty P(X = k) = p^n \sum_{k=0}^\infty \frac{(n+k-1)!}{k!(n-1)!} (1-p)^k.
   $$

3. **Factoren buiten de som halen**:
   Omdat $p^n$ en $(n-1)!$ constanten zijn:

   $$
   \sum_{k=0}^\infty P(X = k) = \frac{p^n}{(n-1)!} \sum_{k=0}^\infty \frac{(n+k-1)!}{k!} (1-p)^k.
   $$

4. **Herken de reeks als een genererende functie**:
   De negatieve binomiale reeks heeft een bekende vorm:

   $$
   \sum_{k=0}^\infty \binom{n+k-1}{k} x^k = \frac{1}{(1-x)^n}, \quad \text{voor } |x| < 1.
   $$

   Hier is $x = 1-p$, dus:

   $$
   \sum_{k=0}^\infty \binom{n+k-1}{k} (1-p)^k = \frac{1}{p^n}.
   $$

5. **Substitueer de reeks in de som**:
   Vervang de som door het resultaat:
   $$
   \sum_{k=0}^\infty P(X = k) = \frac{p^n}{(n-1)!} \cdot \frac{(n-1)!}{p^n} = 1.
   $$

### Conclusie

We hebben aangetoond dat de totale kans van $X \sim NB(n, p)$ gelijk is aan 1:

$$
\sum_{k=0}^\infty P(X = k) = 1.
$$

## Gegeven twee poissonverdelingen $P(\lambda 1), P(\lambda 2)$. Bewijs dat $P(\lambda 1 + \lambda 2) = k$ en dat dit nog steeds poissonverdeeld is.

Om te bewijzen dat de som van twee onafhankelijke Poissonverdelingen $P(\lambda_1)$ en $P(\lambda_2)$ weer een Poissonverdeling is met parameter $\lambda_1 + \lambda_2$, voeren we de volgende stappen uit:

### 1. Definitie van een Poissonverdeling

De kansfunctie van een Poissonverdeling met parameter $\lambda$ is gegeven door:

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \dots
$$

Hieruit volgt dat voor $X_1 \sim P(\lambda_1)$ en $X_2 \sim P(\lambda_2)$, de kansfuncties respectievelijk zijn:

$$
P(X_1 = k_1) = \frac{\lambda_1^{k_1} e^{-\lambda_1}}{k_1!}, \quad P(X_2 = k_2) = \frac{\lambda_2^{k_2} e^{-\lambda_2}}{k_2!}.
$$

We willen aantonen dat de som $X = X_1 + X_2$ een Poissonverdeling $P(\lambda_1 + \lambda_2)$ volgt.

### 2. Eigenschap van de som van onafhankelijke Poisson-verdelingen

Omdat $X_1$ en $X_2$ onafhankelijk zijn, is de gezamenlijke kans dat $X_1 = k_1$ en $X_2 = k_2$:

$$
P(X_1 = k_1, X_2 = k_2) = P(X_1 = k_1) \cdot P(X_2 = k_2).
$$

De som $X = X_1 + X_2$ kan gelijk zijn aan $k$ als $X_1 = k_1$ en $X_2 = k_2$, waarbij $k_1 + k_2 = k$. De kans dat $X = k$ is dus de som van alle mogelijke paren $(k_1, k_2)$ waarvoor $k_1 + k_2 = k$:

$$
P(X = k) = \sum_{k_1=0}^k P(X_1 = k_1) \cdot P(X_2 = k - k_1).
$$

### 3. Invullen van de kansfunctie

Invullen van de kansfuncties voor $X_1$ en $X_2$ geeft:

$$
P(X = k) = \sum_{k_1=0}^k \frac{\lambda_1^{k_1} e^{-\lambda_1}}{k_1!} \cdot \frac{\lambda_2^{k - k_1} e^{-\lambda_2}}{(k - k_1)!}.
$$

### 4. Samenvoegen van termen

Omdat $e^{-\lambda_1}$ en $e^{-\lambda_2}$ onafhankelijk zijn van de som, kunnen we deze buiten de som plaatsen:

$$
P(X = k) = e^{-(\lambda_1 + \lambda_2)} \sum_{k_1=0}^k \frac{\lambda_1^{k_1}}{k_1!} \cdot \frac{\lambda_2^{k - k_1}}{(k - k_1)!}.
$$

Gebruik nu de eigenschap van de binomiale coëfficiënt: $\frac{1}{k!} = \frac{1}{k_1! (k - k_1)!}$. Dit geeft:

$$
P(X = k) = e^{-(\lambda_1 + \lambda_2)} \frac{1}{k!} \sum_{k_1=0}^k \binom{k}{k_1} \lambda_1^{k_1} \lambda_2^{k - k_1}.
$$

### 5. Herken de binomiale stelling

De som in de bovenstaande vergelijking is de binomiale stelling:

$$
(\lambda_1 + \lambda_2)^k = \sum_{k_1=0}^k \binom{k}{k_1} \lambda_1^{k_1} \lambda_2^{k - k_1}.
$$

Hiermee wordt:

$$
P(X = k) = e^{-(\lambda_1 + \lambda_2)} \frac{(\lambda_1 + \lambda_2)^k}{k!}.
$$

### 6. Conclusie

De kansfunctie $P(X = k) = \frac{(\lambda_1 + \lambda_2)^k e^{-(\lambda_1 + \lambda_2)}}{k!}$ komt overeen met die van een Poissonverdeling met parameter $\lambda_1 + \lambda_2$. Dit bewijst dat $X \sim P(\lambda_1 + \lambda_2)$.

# H6: Boolean algebra

## (2x) Wat is het dualiteitsprincipe? Leg uit a.d.h.v. de terminologie. Toon aan en geef alle definities die in deze eigenschap voorkomen (verduidelijk).

Het **dualititeitsprincipe** is een fundamentele eigenschap in de wiskunde, met name in de projectieve meetkunde, logica en algebra. Het principe stelt dat bij veel wiskundige structuren of systemen een uitspraak geldig blijft als bepaalde begrippen worden verwisseld met hun "duale" tegenhangers. Het is bijzonder nuttig omdat het betekent dat het bewijs van een eigenschap vaak automatisch leidt tot het bewijs van een andere eigenschap.

Hieronder bespreken we het dualiteitsprincipe in de context van projectieve meetkunde, omdat het daar klassiek het meest wordt toegepast. Daarna volgen de relevante definities en een bewijs.

### 1. **Dualiteitsprincipe in de projectieve meetkunde**

In de projectieve meetkunde stelt het dualiteitsprincipe dat:

- Elke ware stelling blijft waar als de begrippen **punt** en **lijn** worden verwisseld, en de relaties **liggen op** en **gaan door** worden aangepast.

Bijvoorbeeld:

- In een projectief vlak kunnen uitspraken als "Twee punten bepalen een unieke lijn" worden gedualiseerd tot "Twee lijnen snijden elkaar in precies één punt".

#### Waarom werkt dit?

De axioma's van de projectieve meetkunde (zoals het bestaan van unieke punten en lijnen, samen met hun snijpunten) zijn symmetrisch: punten en lijnen spelen een soortgelijke rol.

### 2. **Belangrijke definities**

#### a) **Projectieve meetkunde**

De projectieve meetkunde is een wiskundige structuur waarin de volgende axioma's gelden:

1. Twee punten bepalen een unieke lijn.
2. Twee lijnen snijden elkaar in een uniek punt.
3. Er bestaan minstens vier punten, waarvan er geen drie collineair zijn (niet op één lijn liggen).

#### b) **Dualiteit**

Dualiteit in een projectief vlak betekent dat je elk **punt** vervangt door een **lijn**, en elke **lijn** vervangt door een **punt**, waarbij de relatie van "liggen op" of "gaan door" behouden blijft. Voorbeelden:

- Een punt $A$ dat op een lijn $l$ ligt, wordt gedualiseerd tot een lijn $l^*$ die door een punt $A^*$ gaat.
- Een uitspraak zoals "drie punten zijn collineair" wordt gedualiseerd tot "drie lijnen zijn concurrent" (dwz, ze snijden elkaar in één punt).

#### c) **Collineariteit en concurrentie**

- **Collineariteit**: Drie of meer punten liggen op één lijn.
- **Concurrentie**: Drie of meer lijnen gaan door één punt.

### 3. **Toon het dualiteitsprincipe aan**

#### a) Originele stelling

Laten we de stelling nemen:

- "Twee punten bepalen een unieke lijn."

**Bewijs**: In de projectieve meetkunde geldt dat voor twee punten $P_1$ en $P_2$, er een unieke lijn $l$ bestaat die door beide punten gaat. Dit volgt uit de axioma's van projectieve meetkunde.

#### b) Gidualiseerde stelling

De duale stelling is:

- "Twee lijnen snijden elkaar in precies één punt."

**Bewijs**: In de projectieve meetkunde geldt dat voor twee lijnen $l_1$ en $l_2$, er een uniek punt $P$ bestaat waar beide lijnen elkaar snijden. Ook dit volgt uit de axioma's van projectieve meetkunde.

Omdat de stelling en haar duale vorm beide waar zijn, is het dualiteitsprincipe aangetoond.

### 4. **Voorbeelden van het dualiteitsprincipe**

#### a) Voorbeeld 1: Driehoeksconfiguratie

- Originele uitspraak: "De drie zijden van een driehoek snijden elkaar in drie punten."
- Duale uitspraak: "De drie hoeken van een driehoek worden bepaald door drie lijnen."

#### b) Voorbeeld 2: Meetkundige plaats

- Originele uitspraak: "De verzameling punten op een cirkel bepaalt een meetkundige plaats."
- Duale uitspraak: "De verzameling lijnen die door een vast punt gaan, bepaalt een meetkundige plaats."

### 5. **Conclusie**

Het dualiteitsprincipe is een krachtig concept dat symmetrie en eenvoud in wiskundige structuren benadrukt. Door het begrip dualiteit toe te passen, kan men veel eigenschappen in één klap begrijpen door uitspraken en hun duale versies te combineren.

# H7: Genererende functies

## $\sum_{k=0}^{n} k*\binom{n}{k}$. Geef een gesloten formule hiervoor en bewijs.

## Genererende functies: Reken een rijtje uit. (Je kreeg een rij, maar er kwamen geen getallen in voor, enkel symbolen)

## Wat is een genererende functie en de inverse ervan? Wanneer bestaat de inverse niet? Bewijs.

## $S_0, a, b$ gegeven: Geef de niet-recursieve formule voor $S_n = a S_{n-1} + b$. Bewijs.

## $\sum_{k=0}^{n} k*\binom{n}{k}$. Geef een gesloten formule hiervoor en bewijs.

## $S_0, a, b$ gegeven: Geef de niet-recursieve formule voor $S_n = a S_{n-1} + b$. Bewijs.

# Niet voor 2024

## Geef de wet van grote getallen en bewijs. Geef ook Chebychev.
