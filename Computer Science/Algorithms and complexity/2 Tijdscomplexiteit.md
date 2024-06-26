# 2.1 Deterministisch polynomiale tijd (PTIME)

**Deterministische Tijd(DTIME):** functie die de tijdcomplexiteit beschrijft van een deterministische Turing-machine. Voor een gegeven functie $f(n)$, is DTIME($f(n)$) de klasse van talen die door een deterministische Turing-machine binnen $f(n)$ stappen kunnen worden besloten voor een invoer van grootte $n$.

$DTIME(t(n)) = \{L ∣ \text{de taal L wordt beslist door een } O(t(n))-\text{tijd deterministische Turing machine met  een tape}\}$

DTIME biedt een gedetailleerdere maatstaf voor complexiteit, waarbij specifieke tijdsgrenzen worden aangegeven in plaats van de algemene polynomiale vorm. Bijvoorbeeld, DTIME($n$), DTIME($n^2$) en DTIME($2^n$) zijn specifieke klassen waar de tijdcomplexiteit respectievelijk lineair, kwadratisch en exponentieel is.

**Polynomiale tijdcomplexiteit**: Een algoritme heeft een polynomiale tijdcomplexiteit als de tijd die nodig is om een invoer van grootte n te verwerken, kan worden uitgedrukt als een polynoom p(n) in n.

**Polynomiale Tijd (PTIME)**: verwijst naar de verzameling beslissingsproblemen die kunnen worden opgelost door een deterministische Turing-machine met één tape in polynomiale tijd. Dit betekent dat er een polynoom $p(n)$ bestaat zodanig dat voor een invoer van grootte $n$, de machine het probleem kan oplossen in maximaal $p(n)$ stappen.

$PTIME = \underset{k} \cup DTIME (n^k)$

Problemen in PTIME worden als efficiënt oplosbaar beschouwd omdat hun looptijd hoogstens polynomiaal groeit met de grootte van de invoer.

**Exhaustieve enumeratie**: een probleemoplossingstechniek waarbij alle mogelijke oplossingen systematisch worden gegenereerd en onderzocht om de gewenste oplossing te vinden.

Alle deterministische berekeningsmodellen zijn polynomiaal equivalent (d.w.z. dat deze modellen kunnen in elkaar worden getransformeerd in polynomiale tijd) 

Voorbeeld:
Veronderstel dat je computer 100 miljoen stappen doet per seconde.
De onderstaande tabel toont de CPU tijd voor verschillende functies t ∶ N → N.

![[Screenshot 2024-06-25 at 14.27.53.png]]

**Representatie van een object** x: $\langle x \rangle$ is een gestructureerde en systematische beschrijving of codering van dat object, waarbij specifieke kenmerken, eigenschappen, en/of relaties worden vastgelegd volgens een bepaalde conventie of afspraak.

Voorbeeld:
Voor een geheel getal n nemen we meestal $\langle n \rangle$ als de binaire representatie van dat getal

**Ongerichte graaf** $G = (V, E)$ bestaat uit:
- $V$: Een verzameling knopen (vertices).
- $E$: Een verzameling randen (edges), waar elke rand een ongeordend paar $\{u, v\}$ van knopen uit $V$ vertegenwoordigt.

Formeel:
$G = (V, E)$ waarbij $E \subseteq \{\{u, v\} \mid u, v \in V \text{ en } u \neq v\}$.

**Gerichte graaf** $G = (V, E)$ bestaat uit:
- $V$: Een verzameling knopen (vertices).
- $E$: Een verzameling gerichte randen (directed edges), waar elke gerichte rand een geordend paar $(u, v)$ van knopen uit $V$ vertegenwoordigt, waarbij $u$ de startknoop (beginpunt) is en $v$ de eindknoop (eindpunt).

Formeel:
$G = (V, E)$ waarbij $E \subseteq \{(u, v) \mid u, v \in V \text{ en } u \neq v\}$.

### Belangrijkste Verschillen

- **Richting van Randen**: In een ongerichte graaf hebben de randen geen specifieke richting; ze vertegenwoordigen tweerichtingsverbindingen tussen knopen. In een gerichte graaf hebben de randen een specifieke richting, van een startknoop naar een eindknoop.

Voorbeeld gerichte graaf
![[Screenshot 2024-06-25 at 14.59.28.png]]


$PATH = \{ \langle G,s,t \rangle | G \text { is een gerichte graaf met een pad van vertex s naar t} \}$

Voorbeeld 
*PTIME algoritme*: Breadth-first search.
M = Op input $\langle G,s,t  \rangle$ met G een gerichte graaf met beginknoop s en eindknoop t:
1. Markeer de startknoop s (**eenmaal**)
2. Herhaal tot geen nieuwe markeringen op knopen gemaakt kunnen worden (**m-keer**)
3. Doorloop de bogen in G. Als (aub) een boog is met gemarkeerde knoop a en niet gemarkeerde knoop b, dan markeer b
4. Als de eindknoop t gemarkeerd is dan aanvaard de input zonet verwerp (**eenmaal**)

- Stappen 1 en 4 zijn in polynomiale tijd.
- Stap 3 vraagt om de input te scannen en te testen welke knopen gemarkeerd zijn, dit kan ook in polynomiale tijd
- Stap 4 herhalen we m keer (m aantal knopen)

# 2.2 Satisfiability problemen
**Satisfiability problemen (SAT)**: een probleem waarbij wordt gevraagd of er een toekenning van waarheidswaarden bestaat aan de variabelen van een gegeven Booleaanse formule, zodanig dat de hele formule waar (satisfied) wordt.

**Propositionele formule** $\rho$ is een uitdrukking die inductief gedefinieerd, is als volgt,
▸ een (propositionele) veranderlijke in $X = \{x_1, x_2, ..., x_k\}$ is een formule;
▸ als $\rho$ een formule is dan is ook ($\neg\rho$) een formule (negatie); en
▸ als $\rho_1$ en $\rho_2$ formules zijn, dan zijn ook ($\rho_1 \wedge \rho_2$) (conjunctie) en ($\rho_1 \vee \rho_2$) (disjunctie) formules.

**Truth assignment**: een functie $ν ∶ X \rightarrow {0, 1}$ van veranderlijken in X naar 0 (onwaar) en 1 (waar).

Gegeven een propositionele formule φ over veranderlijken in X en een truth assignment ν ∶ X → {0, 1}. We definiëren inductief wanneer $ν$ de formule $φ$ **waar maakt** (genoteerd als $ν \models φ$):
- Als $φ$ een veranderlijke $x ∈ X$ is, dan $ν \models φ$ als en slechts dan $ν(x)=1$; 
- Als $φ=(¬ψ)$, dan $ν ƒφ$ als en slechts dan $ν \not\models ψ$;
- Als $φ=(ψ1∧ψ2)$, dan $ν\modelsφ$ als en slechts dan $ν\modelsψ1$ en $ν\modelsψ2$;
- Als $φ=(ψ1 ∨ψ2)$, dan $ν \modelsφ$ als en slechts dan $ν \modelsψ1$ of $ν \modelsψ2$.

Voorbeeld:
Stel $ν(x1)=1$, $ν(x2)=0$ en $ν(x3)=0$, 
dan $ν ⊧/ Φ1$ en $ν ⊧ Φ2$,
met $Φ1 =((x1 ∧x2)∨x3)$ en $Φ2 =(((¬x1)∨(¬x2))∧(x1 ∨x3))→(x2 ∨(¬x3))$.

**Satisfiability**: Een propositionele formule $φ$ is satisfiable als er een truth assignment $ν$ over de veranderlijken in $φ$ bestaat zodat $ν \models φ$, en **unsatisfiable** als er geen truth assignment bestaat die $φ$ waar maakt.

**Equivalentie van formules**: Twee propositionele formules $φ$ en $ψ$ over dezelfde veranderlijken zijn equivalent, genoteerd als $φ ≡ ψ$, als $ν \models φ$ als en slechts dan $ν \models ψ$, voor elke truth assignment ν van de veranderlijken.

**Conjunctieve normaalvorm (CNF)**: Een propositionele formule $φ$ over $X$ is in conjunctieve normaalvorm als die van de vorm$^a$ $φ = C1 ∧ C2 ∧ ⋯ ∧ Cn$, is, waarin clauses $C_i$ zijn, met elke clause van de vorm $C_i =l^i_1 \lor l^i_2 \lor⋯\lor l^i_{p_i}$, met daarin $l^i_j$ literals. Een literal is ofwel een veranderlijke (positive literal x) of een negatie van een veranderlijke (negatieve literal $¬x$ of $\overline{x}$) in X 