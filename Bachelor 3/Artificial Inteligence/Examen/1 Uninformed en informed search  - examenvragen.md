## 1 Vul volgende tabel aan

| **Algorithm**            | **Time Complexity**         | **Space Complexity**        | **Complete** | **Optimal**              |
| ------------------------ | --------------------------- | --------------------------- | ------------ | ------------------------ |
| **Depth-First Search**   | $O(b^m)$                    | $O(bm)$                     | No           | No                       |
| **Breadth-First Search** | $O(b^s)$                    | $O(b^s)$                    | Yes          | Yes (if costs are equal) |
| **Uniform Cost Search**  | $O(b^{(C*/ε)})$             | $O(b^{(C*/ε)})$             | Yes          | Yes                      |
| **Iterative Deepening**  | $O(b^s)$                    | $O(bs)$                     | Yes          | Yes                      |
| **Greedy Search**        | $O(b^m)$                    | $O(b^m)$                    | No           | No                       |
| **A\* Search**           | $O(b^m)$ or $O(b^{(C*/ε)})$ | $O(b^m)$ or $O(b^{(C*/ε)})$ | Yes          | Yes                      |

## 2 Zijn de volgende algorithmes optimaal? Bewijs of geef een tegenvoorbeeld.

### 2.1 Depth-First Search (DFS)

**Is het optimaal?**
Nee, Depth-First Search is niet optimaal.

**Reden:**
DFS kan een oplossing vinden, maar het zoekt niet systematisch naar de goedkoopste of kortste oplossing. Het kan een oplossing vinden die veel duurder is dan een andere.

**Tegenvoorbeeld:**
Beschouw een graaf waarin het eerste pad dat DFS tegenkomt, een totale kost van 10 heeft, maar er is een ander pad met een kost van 2 dat DFS niet onderzoekt omdat het te diep in een ander deel van de graaf zoekt.

### 2.2 Breadth-First Search (BFS)

**Is het optimaal?**
Ja, maar alleen als alle kosten gelijk zijn.

**Reden:**
BFS doorzoekt alle paden van een gegeven lengte voordat het naar langere paden gaat. Als alle stappen dezelfde kosten hebben (uniforme gewichten), vindt BFS gegarandeerd de kortste oplossing.

**Tegenvoorbeeld:**
Als de kosten van de stappen variëren, kan BFS niet garanderen dat het de goedkoopste oplossing vindt. Een pad met veel goedkope stappen kan worden genegeerd in favoriet van een kort pad met dure stappen.

### 2.3 Uniform Cost Search (UCS)

**Is het optimaal?**
Ja, Uniform Cost Search is optimaal, zolang de kosten positief zijn.

**Reden:**
UCS gebruikt een prioriteitsqueue en onderzoekt altijd de goedkoopste nog niet onderzochte knoop. Dit garandeert dat de goedkoopste oplossing wordt gevonden.

**Bewijs:**
Bij UCS worden paden in oplopende volgorde van kosten onderzocht. Wanneer UCS een doeltoestand bereikt, is dit gegarandeerd het goedkoopste pad, omdat alle goedkopere paden al eerder zijn onderzocht.

### 2.4 Iterative Deepening (IDDFS)

**Is het optimaal?**
Ja, maar alleen als alle kosten gelijk zijn.

**Reden:**
Iterative Deepening is een combinatie van DFS en BFS. Het onderzoekt alle paden van een bepaalde lengte voordat het verder gaat, wat overeenkomt met BFS. Als de kosten van de stappen uniform zijn, vindt IDDFS gegarandeerd de kortste oplossing.

**Tegenvoorbeeld:**
Bij variabele kosten kan IDDFS niet garanderen dat het de goedkoopste oplossing vindt, omdat het geen rekening houdt met de werkelijke kosten van de stappen.

### 2.5 Greedy Search

**Is het optimaal?**
Nee, Greedy Search is niet optimaal.

**Reden:**
Greedy Search kiest op basis van een heuristiek die niet noodzakelijk de werkelijke kosten minimaliseert. Het kan hierdoor een oplossing kiezen die lokaal het beste lijkt, maar globaal suboptimaal is.

**Tegenvoorbeeld:**
Stel dat de heuristiek suggereert om een pad te volgen dat dichter bij het doel lijkt, terwijl een ander pad met een lagere kost verder weg ligt. Greedy Search negeert dat goedkopere pad.

### 2.6 A\* Search

**Is het optimaal?**
Ja, zolang de heuristiek consistent (monotoon) is en de kosten positief zijn.

**Reden:**
A* combineert UCS (minimale kosten) en een heuristiek (schatting van resterende kosten). Als de heuristiek consistent is, is A* gegarandeerd optimaal omdat het de kosten van elk pad systematisch onderzoekt en alleen stopt wanneer de goedkoopste oplossing is gevonden.

**Bewijs:**
A* houdt een prioriteitsqueue bij en gebruikt de functie $f(n) = g(n) + h(n)$, waarbij $g(n)$ de huidige kost is en $h(n)$ de heuristische schatting van de resterende kosten. Een consistente heuristiek zorgt ervoor dat A* geen suboptimale oplossing accepteert.

Als samenvatting:

| Algoritme            | Optimaal?           | Voorwaarden                                       |
| -------------------- | ------------------- | ------------------------------------------------- |
| Depth-First Search   | Nee                 | -                                                 |
| Breadth-First Search | Ja (gelijke kosten) | Alle stappen hebben dezelfde kosten.              |
| Uniform Cost Search  | Ja                  | Kosten zijn positief.                             |
| Iterative Deepening  | Ja (gelijke kosten) | Alle stappen hebben dezelfde kosten.              |
| Greedy Search        | Nee                 | -                                                 |
| A\* Search           | Ja                  | Heuristiek is consistent en kosten zijn positief. |

## 3 Gegeven een spel geef het beste zoekalgoritme

### 3.1 Minimaliseren van aantal stappen om auto's te verschuiven zodat een specifieke auto de uitgang bereikt

**Beste zoekalgoritme:**
Iterative Deepening

**Reden:**
Iterative Deepening combineert de voordelen van Breadth-First Search (BFS) en Depth-First Search (DFS). Het doorzoekt de zoekruimte in toenemende diepte, waardoor het de oplossing vindt met het minimale aantal stappen. Dit is cruciaal voor spellen zoals Rush Hour, waar de oplossing vaak afhankelijk is van de kortste reeks zetten. Omdat het volledige niveau’s doorzoekt, is het gegarandeerd optimaal en efficiënt in geheugengebruik.

**Hoe te gebruiken:**

1. Stel een maximale diepte in en begin vanaf diepte 0.
2. Gebruik DFS tot de ingestelde diepte.
3. Verhoog de diepte iteratief en herhaal het proces.
4. Stop wanneer de oplossing is gevonden.

### 3.2 Bepalen van de beste zet in een schaakpositie (minimax met alpha-beta pruning)

**Beste zoekalgoritme:**
Minimax met Alpha-Beta Pruning

**Reden:**
Dit algoritme is specifiek ontworpen voor beslissingsproblemen met twee spelers. Minimax analyseert mogelijke zetten en hun gevolgen door de zoekboom te evalueren. Alpha-Beta Pruning optimaliseert dit proces door delen van de boom te elimineren die niet bijdragen aan het eindresultaat. Dit bespaart tijd zonder dat het de nauwkeurigheid beïnvloedt.

**Hoe te gebruiken:**

1. Genereer de zoekboom van mogelijke zetten.
2. Gebruik de minimax-strategie om elk niveau van de boom te evalueren:
   - Maximaliseer de score voor jouw zetten.
   - Minimaliseer de score voor de tegenstander.
3. Pas Alpha-Beta Pruning toe om onnodige berekeningen te vermijden.
4. Selecteer de zet met de hoogste score.

### 3.3 Het oplossen van een puzzel waarbij alle stukken in een specifieke volgorde moeten worden geplaatst (bijvoorbeeld Sudoku)

**Beste zoekalgoritme:**
Constraint Satisfaction Problem (CSP)-technieken met Backtracking

**Reden:**
CSP-technieken zijn ideaal voor puzzels waarin variabelen moeten voldoen aan specifieke beperkingen. Backtracking is een systematische manier om alle mogelijke combinaties te proberen totdat de oplossing is gevonden. Door slimme technieken zoals Forward Checking en Constraint Propagation toe te passen, kan het algoritme efficiënter zoeken.

**Hoe te gebruiken:**

1. Definieer de variabelen en beperkingen van de puzzel.
2. Begin met een lege puzzel en probeer waarden toe te wijzen aan elke variabele:
   - Controleer telkens of de huidige toewijzing voldoet aan de beperkingen.
3. Als een beperking wordt geschonden, maak een stap terug (backtracking).
4. Ga door tot de puzzel is opgelost.

### 3.4 Verkennen van een onbekende omgeving (bijvoorbeeld een doolhof)

**Beste zoekalgoritme:**
A\*

**Reden:**
A\* is een heuristisch zoekalgoritme dat gebruik maakt van een kostenfunctie om efficiënt door een onbekende ruimte te navigeren. Het combineert de daadwerkelijke kosten (g) en een geschatte kost (h) om de optimale oplossing te vinden. Het is vooral krachtig in doolhoven of vergelijkbare situaties waarin de kortste route moet worden bepaald.

**Hoe te gebruiken:**

1. Definieer een startpunt en een eindpunt.
2. Stel de kostenfunctie in:
   - g: de afstand van het startpunt naar het huidige punt.
   - h: een heuristische schatting van de afstand naar het eindpunt.
3. Gebruik een prioriteitsqueue om punten met de laagste geschatte totale kosten (f = g + h) te onderzoeken.
4. Beweeg naar het volgende punt met de laagste f-waarde.
5. Stop wanneer het eindpunt is bereikt.

## 4 Heuristieken

### **4.1 Is elke admissiebele heuristiek consistent?**

Een heuristiek $h(n)$ is:

- **Admissiebel** als $h(n) \leq h^*(n)$ voor elke knoop $n$, waarbij $h^*(n)$ de werkelijke kosten zijn van $n$ naar een doel.
- **Consistent** (of monotone) als $h(n) \leq c(n, n') + h(n')$ voor elke knoop $n$ en zijn buur $n'$, waarbij $c(n, n')$ de kosten zijn van de directe overgang tussen $n$ en $n'$.

#### Bewijs of tegenvoorbeeld:

Niet elke admissiebele heuristiek is consistent. Dit kan worden geïllustreerd met een tegenvoorbeeld:

- Stel een graaf voor met knopen $A, B, C$, waarbij:
  - Kosten $c(A, B) = 1$
  - Kosten $c(B, C) = 2$
  - Kosten $c(A, C) = 4$
- Stel een admissiebele heuristiek $h$ voor:
  - $h(A) = 4$
  - $h(B) = 2$
  - $h(C) = 0$

$h$ is admissiebel omdat $h(n) \leq h^*(n)$ voor elk $n$. Echter, het voldoet niet aan consistentie:

- $h(A) = 4$ en $c(A, B) + h(B) = 1 + 2 = 3$. Hier is $h(A) > c(A, B) + h(B)$, dus de consistentievoorwaarde wordt geschonden.

**Conclusie:** Niet elke admissiebele heuristiek is consistent.

### **4.2 Is elke consistente heuristiek admissiebel?**

#### Bewijs:

Elke consistente heuristiek is ook admissiebel. Dit kan worden bewezen:

1. Uit de definitie van consistentie volgt dat voor elke overgang $(n, n')$:
   $$
   h(n) \leq c(n, n') + h(n')
   $$
2. Voor een pad $n \to n*1 \to n_2 \to \dots \to n_g$ (waarbij $n_g$ een doel is), kunnen we consistentie herhaaldelijk toepassen:
   $$
   h(n) \leq c(n, n_1) + h(n_1) \leq c(n, n_1) + c(n_1, n_2) + h(n_2) \leq \dots \leq c(n, n_1) + c(n_1, n_2) + \dots + c(n*{g-1}, n_g) + h(n_g)
   $$
3. Omdat $h(n_g) = 0$ voor een doeltoestand, geldt:
   $$
   h(n) \leq \text{werkelijke kosten van } n \text{ naar het doel}
   $$
   Dit impliceert dat $h(n)$ admissiebel is.

**Conclusie:** Elke consistente heuristiek is admissiebel.

### **4.3 Voorbeeld van A\* dat niet optimaal is bij een admissiebele heuristiek**

#### Situatie:

Beschouw een graaf met de volgende opzet:

- Knopen: $S, A, B, G$ (waarbij $S$ de start is en $G$ het doel).
- Kosten:
  - $c(S, A) = 1$, $c(A, G) = 5$
  - $c(S, B) = 2$, $c(B, G) = 2$
- Heuristiek:
  - $h(S) = 3$, $h(A) = 5$, $h(B) = 1$, $h(G) = 0$

#### A\* uitvoering:

1. Start met $S$, $f(S) = g(S) + h(S) = 0 + 3 = 3$.
2. Vanuit $S$:
   - Naar $A$: $g(A) = 1$, $f(A) = g(A) + h(A) = 1 + 5 = 6$.
   - Naar $B$: $g(B) = 2$, $f(B) = g(B) + h(B) = 2 + 1 = 3$.
   - $B$ wordt als eerst geselecteerd omdat $f(B) < f(A)$.
3. Vanuit $B$ naar $G$: $g(G) = g(B) + c(B, G) = 2 + 2 = 4$, $f(G) = 4$.
4. $G$ wordt bereikt met een totale kosten van 4.

#### Probleem:

Het optimale pad is $S \to A \to G$ met totale kosten $1 + 5 = 6$. Het pad via $B$ is echter $2 + 2 = 4$, wat door A\* wordt gekozen. Dit komt doordat de heuristiek niet consistent is.

**Conclusie:** A\* is niet gegarandeerd optimaal als de heuristiek alleen admissiebel is.
