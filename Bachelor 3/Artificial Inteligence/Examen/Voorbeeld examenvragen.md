# Uninformed en informed search

## Vul volgende tabel aan. De tabel bevat voor verschillende zoekalgoritmes de tijds- en ruimtecomplexiteit, of het algoritme al dan niet compleet is (steeds een doelnode vindt als die er is), en al dan niet optimaal is (steeds het kortste pad naar de meest dichtstbijzijnde doelnode vindt). Veronderstel dat de doelnode gezocht wordt in een eindige boom met diepte m, waarbij elke node die geen blad is, b kinderen heeft:

| Algoritme            | Tijdscomplexiteit | Ruimtecomplexiteit | Compleet | Optimaal |
| -------------------- | ----------------- | ------------------ | -------- | -------- |
| Breadth-First Search | $O(b^m)$          | $O(b^m)$           | Ja       | Ja       |
| Depth-First Search   | $O(b^m)$          | $O(bm)$            | Nee      | Nee      |
| Iterative Deepening  | $O(b^d)$          | $O(bd)$            | Ja       | Ja       |

## Is het uniform cost search algoritme optimaal (vindt het steeds het kortste pad tot een doelnode)? Bewijs of geef een tegenvoorbeeld.

Ja, het **Uniform Cost Search (UCS)** algoritme is optimaal, mits aan bepaalde voorwaarden is voldaan. UCS vindt steeds het kortste pad naar een doelnode in een zoekprobleem waar de kosten van de randen (edge costs) niet negatief zijn. Hier is een bewijs voor de optimaliteit en de reden waarom negatieve gewichten problemen kunnen veroorzaken:

### **Bewijs voor optimaliteit van UCS**

1. **Eigenschap van UCS:**
   UCS is een variatie van een breedte-eerst zoekalgoritme dat prioriteit geeft aan de kosten van het pad. Het gebruikt een **prioriteitsqueue** waarin nodes worden gesorteerd op basis van de cumulatieve kosten vanaf de startnode tot de huidige node.

2. **Optimaliteit door prioriteitsqueue:**

   - Bij UCS wordt altijd de node met de laagste cumulatieve kosten als eerste verwerkt.
   - Wanneer een doelnode wordt bereikt, is het pad naar die doelnode gegarandeerd minimaal. Dit komt doordat UCS de kosten van alle mogelijke paden naar elke node in oplopende volgorde verwerkt. Zodra een doelnode wordt geselecteerd, zijn er geen kortere paden meer mogelijk.

3. **Geen negatieve gewichten:**
   UCS veronderstelt dat de gewichten van de randen (edge costs) niet negatief zijn. Dit zorgt ervoor dat eenmaal verwerkte nodes niet opnieuw verwerkt hoeven te worden, omdat een pad niet korter kan worden na het toevoegen van extra positieve kosten.

4. **Conclusie:**
   Aangezien UCS altijd de goedkoopste optie kiest en dit proces voortzet tot de doelnode wordt bereikt, is het gegarandeerd dat UCS het kortste pad vindt.

### **Tegenvoorbeeld met negatieve gewichten**

Als er negatieve gewichten in de graaf zijn, kan UCS falen. Dit komt doordat een pad dat eerder als optimaal werd beschouwd, later overschreven kan worden door een pad met een lagere cumulatieve kosten.

#### Voorbeeld:

Overweeg de volgende graaf met negatieve gewichten:

- Start: $A$
- Doel: $D$
- Randen en kosten:
  - $A \to B$ met kosten $1$
  - $B \to C$ met kosten $2$
  - $C \to D$ met kosten $-4$
  - $A \to D$ met kosten $5$

**Stap-voor-stap UCS:**

1. UCS begint bij $A$ en zet $B$ (kosten 1) en $D$ (kosten 5) in de prioriteitsqueue.
2. $B$ wordt verwerkt, en $C$ wordt toegevoegd met cumulatieve kosten $1 + 2 = 3$.
3. $C$ wordt verwerkt, en $D$ wordt toegevoegd met cumulatieve kosten $3 + (-4) = -1$.
4. Uiteindelijk kiest UCS $D$ met de negatieve kosten $-1$, wat het correcte resultaat lijkt.

**Probleem:**
Als $A \to B \to C \to D$ meerdere keren verwerkt moet worden vanwege negatieve gewichten, kan UCS in een oneindige lus terechtkomen. Hierdoor wordt het algoritme inefficiënt en mogelijk niet optimaal.

### **Conclusie**

Uniform Cost Search is **optimaal** zolang de graaf geen negatieve gewichten bevat. In het geval van negatieve gewichten is UCS niet gegarandeerd optimaal en kan het falen. In dergelijke gevallen is een ander algoritme, zoals **Bellman-Ford**, beter geschikt.

## Is het best search first algoritme optimaal (vindt het steeds het kortste pad tot een doelnode)? Bewijs of geef een tegenvoorbeeld.

Het **Best First Search** (BFS) algoritme is niet gegarandeerd optimaal, tenzij specifieke voorwaarden worden voldaan. Hieronder wordt dit uitgelegd, gevolgd door een tegenvoorbeeld om de niet-optimaliteit aan te tonen.

### Best First Search (BFS) Algoritme

Best First Search selecteert de volgende te verkennen knoop op basis van een **evaluatiefunctie** $f(n)$. Deze evaluatiefunctie kan gebaseerd zijn op verschillende heuristieken, bijvoorbeeld de geschatte afstand tot de doelknoop.

- **Optimaliteit hangt af van de gebruikte heuristiek**. Als de heuristiek niet consistent of niet minimaal is, kan BFS niet garanderen dat het het kortste pad vindt.

### Voorwaarden voor Optimaliteit

1. **Heuristiek is consistent**: Een heuristiek is consistent als voor elke knoop $n$ en een buurknop $n'$, geldt dat:
   $$
   h(n) \leq c(n, n') + h(n')
   $$
   waarbij $h(n)$ de geschatte kost is van $n$ naar het doel, en $c(n, n')$ de werkelijke kost tussen $n$ en $n'$.
2. **Heuristiek is minimaal**: Dit betekent dat $h(n) \leq h^{*}_(n)$, waarbij $h^_(n)$ de werkelijke minimale kost is van $n$ naar het doel.

Als de heuristiek inconsistent is of overschat, kan BFS een suboptimaal pad kiezen omdat het verkeerde knopen prioriteert.

### Tegenvoorbeeld

Laten we een graaf beschouwen waarin de heuristiek niet consistent is.

#### Graaf:

- Knopen: $A, B, C, D$
- Paden:
  - $A \to B$ met kost $1$
  - $A \to C$ met kost $5$
  - $B \to D$ met kost $10$
  - $C \to D$ met kost $1$
- Heuristiek ($h$):
  - $h(A) = 6$
  - $h(B) = 4$
  - $h(C) = 2$
  - $h(D) = 0$ (doelknoop)

#### Verkenning met BFS:

1. Begin bij $A$, kies knoop met laagste $h$:
   - $h(B) = 4$, $h(C) = 2$
   - Knoop $C$ wordt gekozen (laagste $h$).
2. Ga naar $C$, kies volgende stap:
   - Vanuit $C \to D$, totale kost $5 + 1 = 6$.

#### Kortste pad:

Het kortste pad is $A \to B \to D$ met totale kost $1 + 10 = 11$. Echter, BFS kiest $A \to C \to D$ met totale kost $6$, wat suboptimaal is.

### Conclusie

Het Best First Search algoritme is niet optimaal tenzij een consistente en minimale heuristiek wordt gebruikt. In het bovenstaande tegenvoorbeeld toont de inconsistente heuristiek aan dat BFS een suboptimaal pad kiest.

## In het populaire spelletje “Rush hour” moet je een wagentje proberen te bevrijden uit een parking waarbij je de wagens enkel vooruit of achteruit mag bewegen. In de volgende beginsituatie moet je de oranje wagen uit de uitgang rechts zien te rijden.

Dit kan je als volgt doen:

1. Rijd de blauwe wagen 1 plaats naar boven
2. Rijd de grijze wagen helemaal naar rechts
3. Beweeg de grote gele wagen 1 plaats naar onder
4. Nu kan de oranje wagen drie plaatsen vooruit
5. Beweeg de grote gele wagen terug 1 plaats naar boven
6. De grijze wagen gaat 1 plaatsje terug naar links
7. Blauw terug naar beneden
8. De oranje wagen kan nu buitenrijden

Let op: het aantal stappen om het probleem op te lossen, wordt geteld als het aantal bewegingen. Een wagen 3 plaatsen naar voor schuiven telt als 1 stap. Een wagen 1 stap vooruit en vervolgens terug 1 stap achteruit rijden, telt als 2 stappen. De oplossing hierboven telt dus 8 stappen.

Hier zijn een aantal vragen mogelijk:

1. Met welke techniek die we in de les zagen zou je dit probleem oplossen? Dat is: vind een manier, bij voorkeur de kortste, om de wagen te bevrijden uit de parking. Om volledige punten te krijgen moet jouw oplossingsmethode de efficiëntste zijn die we zagen en voldoende gedetailleerd beschreven zijn. 1
2. Welke van volgende heuristieken voor dit probleem zijn admissiebel? Welke consistent?
   a. H1 : het aantal vakjes dat de oranje wagen verwijderd is van de uitgang
   b. H2: het aantal wagens die op het rechtstreekse pad van de te bevrijden wagen
   staan.
   c. H3: het aantal wagens waarvan minstens 1 blokje zich rechts van de te bevrijden wagen bevindt

### Vraag 1: Oplossingstechniek

Om het probleem van "Rush Hour" op te lossen, gebruiken we een **heuristische zoekalgoritme**, bij voorkeur het **A\*-algoritme**. HetA\*-algoritme garandeert dat we de kortste weg vinden, zolang de gebruikte heuristiek **admissiebel** en **consistent** is. Het algoritme werkt als volgt:

1. **Toestandsruimte modelleren**:

   - Elke toestand beschrijft de huidige posities van alle voertuigen op de parkeerplaats.
   - Een toestand heeft een starttoestand en een doeltoestand (de oranje wagen moet naar de uitgang rechts bewegen).

2. **Acties definiëren**:

   - Elke actie is een beweging van een voertuig naar voren of naar achteren binnen de grenzen van het raster, zonder andere voertuigen te raken.

3. **Kostenfunctie**:

   - Elke beweging (ongeacht de afstand) telt als één stap. De kosten $g(n)$ van een pad is het aantal bewegingen dat nodig is om de huidige toestand $n$ te bereiken.

4. **Heuristiek kiezen**:

   - Gebruik een heuristiek $h(n)$ die de geschatte kost tot het bereiken van de doeltoestand inschat. Een goede heuristiek maakt het algoritme efficiënter.

5. **Totale evaluatiefunctie**:

   - HetA\*-algoritme gebruikt $f(n) = g(n) + h(n)$, waarbij $g(n)$ de al gemaakte kosten zijn en $h(n)$ de geschatte resterende kosten.

6. **Zoekproces**:
   - Begin bij de starttoestand, plaats deze in een prioriteitswachtrij gesorteerd op $f(n)$.
   - Kies de toestand met de laagste $f(n)$, genereer opvolgende toestanden door toegestane acties, en herhaal tot de doeltoestand is bereikt.

HetA\*-algoritme is de efficiëntste methode die we hebben gezien omdat het de kortste oplossing vindt binnen een aanvaardbare tijd, zolang de heuristiek goed gekozen is.

### Vraag 2: Heuristieken

#### Heuristieken analyseren:

Om een heuristiek te gebruiken metA\*, moet deze aan de volgende eigenschappen voldoen:

- **Admissiebel**: Een heuristiek is admissiebel als ze de werkelijke kosten naar de oplossing nooit overschat. Dit garandeert dat hetA\*-algoritme de optimale oplossing vindt.
- **Consistent**: Een heuristiek is consistent als voor elke overgang van toestand $n$ naar toestand $n'$ geldt: $h(n) \leq c(n, n') + h(n')$, waarbij $c(n, n')$ de werkelijke kost is van de overgang. Consistentie garandeert dat $f(n)$ nooit daalt langs een pad.

#### Analyseren van de gegeven heuristieken:

**a. H1: Het aantal vakjes dat de oranje wagen verwijderd is van de uitgang**

- **Admissiebel**: Ja, omdat de oranje wagen minstens zoveel vakjes moet verplaatsen om de uitgang te bereiken. Dit overschat de werkelijke kosten niet.
- **Consistent**: Ja, omdat de afstand tot de uitgang niet kan toenemen bij een geldige beweging.

**b. H2: Het aantal wagens die op het rechtstreekse pad van de te bevrijden wagen staan**

- **Admissiebel**: Ja, omdat elk voertuig op het pad minstens één keer moet bewegen. Dit is een ondergrens van de werkelijke kosten.
- **Consistent**: Ja, omdat het verwijderen van een voertuig nooit meer kost dan één stap per beweging.

**c. H3: Het aantal wagens waarvan minstens één blokje zich rechts van de te bevrijden wagen bevindt**

- **Admissiebel**: Nee, omdat niet al deze wagens noodzakelijkerwijs op het pad van de oranje wagen liggen of bewegen. Dit kan leiden tot een overschatting.
- **Consistent**: Nee, omdat het aantal wagens rechts van de oranje wagen kan afnemen zonder directe actie, wat inconsistente waarden van $h$ kan opleveren.

#### Conclusie:

- $H1$ en $H2$ zijn admissiebel en consistent, en kunnen worden gebruikt metA\*.
- $H3$ is noch admissiebel noch consistent en is niet geschikt.

## Is elke admissiebele heuristiek consistent? Bewijs of geef een tegenvoorbeeld.

Een **admissibele heuristiek** is een heuristiek die nooit de werkelijke kosten onderschat. Formeel betekent dit dat voor een heuristiek $h(n)$ geldt:

$$
h(n) \leq h^{*}(n) \quad \forall n,
$$

waarbij $h^*(n)$ de werkelijke minimale kosten zijn van de huidige toestand $n$ naar een doeltoestand.

De vraag of elke admissibele heuristiek **consistent** is, vereist dat we de definitie van consistentie bekijken. Een heuristiek is consistent (of monotoon) als deze voldoet aan de volgende eigenschap:

$$
h(n) \leq c(n, n') + h(n'),
$$

voor elke toestand $n$, elke opvolger $n'$ van $n$, en de werkelijke kosten $c(n, n')$ van de overgang van $n$ naar $n'$. Dit betekent dat de heuristiekwaarde van een toestand nooit groter mag zijn dan de kosten van de stap plus de heuristiekwaarde van de opvolger.

### Bewijs of tegenvoorbeeld

Laten we onderzoeken of elke admissibele heuristiek consistent is.

#### Tegenvoorbeeld

Een heuristiek kan admissibel zijn zonder consistent te zijn. Overweeg het volgende voorbeeld:

1. Stel dat we een graaf hebben met toestanden $A$, $B$, en $C$.
2. De werkelijke kosten zijn:
   - Van $A$ naar $B$: $c(A, B) = 1$,
   - Van $B$ naar $C$: $c(B, C) = 1$,
   - Van $A$ naar $C$: $c(A, C) = 2$.
3. Definieer de heuristiekwaarden als volgt:
   - $h(A) = 2$,
   - $h(B) = 2$,
   - $h(C) = 0$.

De heuristiek $h$ is admissibel omdat:

$$
h(n) \leq h^{*}(n) \quad \forall n.
$$

- Voor $A$, $h(A) = 2 = h^*(A)$ (de werkelijke minimale kosten naar $C$),
- Voor $B$, $h(B) = 2 = h^*(B)$ (de werkelijke minimale kosten naar $C$),
- Voor $C$, $h(C) = 0 = h^*(C)$.

Echter, $h$ is niet consistent omdat:

$$
h(A) = 2 \nleq c(A, B) + h(B) = 1 + 2 = 3.
$$

Hier schendt de heuristiek de consistentie-eis.

### Conclusie

Niet elke admissibele heuristiek is consistent. Het bovenstaande tegenvoorbeeld toont een situatie waarin een heuristiek admissibel is, maar niet consistent.

## Is elke consistente heuristiek admissiebel? Bewijs of geef een tegenvoorbeeld.

Een consistente heuristiek is niet noodzakelijkerwijs admissiebel, omdat consistentie niet automatisch betekent dat de heuristiek nooit een waarde overschat. Laten we dit zorgvuldig onderzoeken en bewijzen of ontkrachten met behulp van een tegenvoorbeeld.

### Definitie van begrippen:

1. **Consistente heuristiek**:

   - Voor een heuristiek $h(n)$ geldt consistentie als:
     $$
     h(n) \leq c(n, n') + h(n')
     $$
     voor elke overgang van knoop $n$ naar $n'$, waarbij $c(n, n')$ de kosten zijn van de overgang van $n$ naar $n'$.
   - Bovendien moet $h(n) \leq h^{*}_(n)$ bij de doelknoop $n$, waar $h^_(n)$ de exacte kost is.

2. **Admissibele heuristiek**:
   - Een heuristiek $h(n)$ is admissiebel als:
     $$
     h(n) \leq h^{*}_{n}
     $$
     voor elke knoop $n$, waar $h^_(n)$ de exacte minimale kost is van $n$ naar een doelknoop.

### Bewijs of tegenvoorbeeld:

We moeten bepalen of consistentie altijd admissie betekent.

#### Eigenschap 1: Consistentie impliceert admissie

Een consistente heuristiek voldoet automatisch aan $h(n) \leq h^{*}(n)$, omdat de consistentie-eigenschap $h(n) \leq c(n, n') + h(n')$ voorkomt dat de heuristiek ooit een waarde kan overschatten ten opzichte van de werkelijke kosten. Dit kan formeel worden aangetoond door inductie langs een pad van de startknoop naar de doelknoop:

1. Bij de doelknoop $n$: $h(n) = 0$, wat altijd kleiner is dan of gelijk aan $h^{*}(n)$.
2. Voor elke andere knoop $n$ en zijn opvolger $n'$: $h(n) \leq c(n, n') + h(n')$, en door inductie geldt dat $h(n') \leq h^_(n')$. Dit leidt ertoe dat $h(n) \leq h^{*}_(n)$.

#### Conclusie:

Elke consistente heuristiek is per definitie ook admissiebel. Dit betekent dat een consistente heuristiek nooit een overschatting zal geven van de werkelijke kosten naar de doelknoop, en dus altijd admissiebel is.

**Er is geen tegenvoorbeeld mogelijk waarin een consistente heuristiek niet admissiebel is, omdat consistentie sterker is dan admissie.**

## Het A\* algoritme in een graaf die geen boom is, is niet gegarandeerd optimaal als de heuristiek admissiebel is; geef een voorbeeld dat dit illustreert.

Het A*-algoritme is gegarandeerd optimaal als de heuristiek **admissibel** is (d.w.z. dat de heuristiek nooit de werkelijke kosten overschat) en **consistent** (monotoon). Als de heuristiek alleen admissibel is, maar niet consistent, kan het A*-algoritme suboptimale paden genereren in een graaf die geen boom is.

### Voorbeeld

Laten we een voorbeeld beschouwen waarin hetA\*-algoritme faalt bij een admissibele, maar inconsistente heuristiek.

#### Graafstructuur

We hebben de volgende gewogen graaf:

```
        (A)
      /  |  \
   1 /   |2   \3
    /    |     \
 (B)---4---(C)---2---(D)
           \
            \1
             \
             (E)
```

- **Knopen**: A, B, C, D, E
- **Kosten** van de randen worden weergegeven in de graaf.
- De startknoop is **A**, en de doelknoop is **D**.

#### Heuristiek $h(n)$:

De heuristiek is admissibel, maar niet consistent:

- $h(A) = 4$
- $h(B) = 2$
- $h(C) = 1$
- $h(D) = 0$ (altijd 0 bij het doel)
- $h(E) = 3$

#### Werkelijke kortste pad

Het werkelijke kortste pad van $A$ naar $D$ is:
$A \to C \to D$ met totale kosten van $2 + 2 = 4$.

#### Gedrag van hetA\*-algoritme

Bij gebruik van deze heuristiek:

1. **Begin bij A**:

   - $f(A) = g(A) + h(A) = 0 + 4 = 4$

2. **Kandidaten vanuit A**:

   - $B$: $f(B) = g(B) + h(B) = 1 + 2 = 3$
   - $C$: $f(C) = g(C) + h(C) = 2 + 1 = 3$
   - $D$: $f(D) = g(D) + h(D) = 3 + 0 = 3$

   $B$, $C$, en $D$ hebben dezelfde $f$-waarde. Stel dat $A*$ eerst $B$ kiest.

3. **Vanuit B**:
   - Knoop $B$ heeft geen directe verbinding naar $D$ die korter is dan via $A$, dus $A*$ blijft $B$ overwegen, terwijl $C \to D$ overgeslagen wordt.

#### Resultaat

Vanwege de inconsistente heuristiek kiestA\* een suboptimaal pad, afhankelijk van de volgorde waarin knopen worden geëvalueerd. Dit toont aan dat admissibiliteit alleen niet voldoende is om optimale paden te garanderen in een niet-boomstructuur.
