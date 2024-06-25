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

*Representatie van een object* x als woord: $\langle x \rangle$ (object kan een graaf, formule of een getal zijn)

Voor een geheel getal n nemen we meestal $\langle n \rangle$ als de binaire representatie van dat getal

**Ongerichte graaf**: Een graaf waarbij de randen geen richting hebben. Als er een rand is die een knooppunt met een ander verbindt, betekent dit dat de twee knooppunten verbonden zijn, zonder enige richting te impliceren.

**Gerichte graaf**: In tegenstelling tot een ongerichte graaf, hebben de randen in een gerichte graaf een richting. Dit betekent dat als er een rand is van knooppunt A naar knooppunt B, het betekent dat A verbonden is met B, maar niet noodzakelijk vice versa.

$PATH = \{ \langle G,s,t \rangle | G \text { is een gerichte graaf met een pad van vertex s naar t} \}$

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
**Satisfiability problemen**: een klasse van problemen die gaan over het vinden van een toewijzing van waarden aan variabelen die voldoen aan een bepaalde logische formule.

Een propositionele formule $\rho$ is een uitdrukking die inductief gedefinieerd, is als volgt,
▸ een (propositionele) veranderlijke in X = {x1, x2, ..., xk } is een formule;
▸ als $\rho$ een formule is dan is ook ($\neg\rho$) een formule (negatie); en
▸ als $\rho_1$ en $\rho_2$ formules zijn, dan zijn ook ($\rho_1 \wedge \rho_2$) (conjunctie) en ($\rho_1 \vee \rho_2$) (disjunctie) formules.

