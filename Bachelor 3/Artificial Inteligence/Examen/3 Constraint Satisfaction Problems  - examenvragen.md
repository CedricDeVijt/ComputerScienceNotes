## 1 Oplossen van een CSP

### 1.1 Examenrooster

Een examenrooster probleem kan worden opgevat als een Constraint Satisfaction Problem (CSP), waar we een set van variabelen, domeinen en beperkingen hebben:

**Variabelen**

- Elke examen wordt gerepresenteerd door een variabele, bijv. $X_1, X_2, ..., X_n$.

**Domeinen**

- Het domein van elke variabele bestaat uit alle mogelijke combinaties van lokalen en tijdstippen, bijvoorbeeld $(lokaal_1, tijd_1), (lokaal_2, tijd_2), ...$.

**Beperkingen**

- Geen twee examens mogen tegelijk in hetzelfde lokaal plaatsvinden.
- Examen X moet plaatsvinden op tijdstip $T$ indien dat opgelegd is.
- Indien een examen een computerlokaal vereist, mag het enkel toegewezen worden aan lokalen met computers.

**Oplossingsmethode**

1. **Modeleren als CSP**: Gebruik een representatie met variabelen, domeinen, en beperkingen.
2. **Forward Checking**: Elimineer onmiddellijk waarden uit domeinen die in strijd zijn met de beperkingen.
3. **Backtracking Search**: Los de CSP iteratief op door variabelen toe te wijzen en terug te keren als een toewijzing niet voldoet.
4. **Constraint Propagation**: Gebruik technieken zoals Arc Consistency (AC-3) om te zorgen dat de constraints lokaal consistent zijn.
5. **Heuristieken**:
   - **Minimum Remaining Values (MRV)**: Kies eerst de variabele met de minste mogelijke waarden.
   - **Least Constraining Value (LCV)**: Kies een waarde die de minste beperkingen oplegt aan andere variabelen.

### 1.2 Kruiswoordraadsel

#### a) Beschrijving als CSP

**Variabelen**

- Elke lege plaats in het kruiswoordraadsel is een variabele. Bijvoorbeeld, $V_1, V_2, ..., V_n$.

**Domeinen**

- Het domein van elke variabele is de set woorden die in de puzzel passen qua lengte.

**Beperkingen**

- Overlappende woorden (bijvoorbeeld een horizontaal en verticaal woord dat dezelfde letter deelt) moeten dezelfde letter hebben.
- Elk woord moet geldig zijn en uit de lijst met toegestane woorden komen.

#### b) Oplossingsmethode

1. **Modeleren als CSP** zoals hierboven beschreven.
2. **Backtracking Search**: Probeer woorden toe te wijzen aan variabelen en ga terug als een beperking wordt geschonden.
3. **Constraint Propagation**: Gebruik technieken zoals Arc Consistency (AC-3) om de domeinen van woorden te verkleinen door te controleren op overlappende letters.
4. **Heuristieken**: Gebruik MRV en LCV om efficiënter een oplossing te vinden.

#### c) Is de CSP boomvormig?

Een kruiswoordraadsel is meestal **geen boomvormige CSP**, omdat variabelen vaak afhankelijk zijn van meerdere andere variabelen (bijvoorbeeld door overlappende letters).

- **Oplossing voor niet-boomvormige CSP**:
  - Converteer de CSP naar een boomvorm met behulp van **tree decomposition**.
  - Gebruik vervolgens een algoritme voor boomvormige CSPs. In dit geval los je de deelproblemen op in een specifieke volgorde en combineer je de oplossingen.

## 2. Eigenschappen van CSP's

### 2.1 Tijdcomplexiteit

Voor boomvormige CSP's is de tijdcomplexiteit $O(nd^2)$:

- **Waarom?**

  - **n**: Het aantal variabelen. Elke variabele wordt slechts één keer verwerkt.
  - **$d^2$**: Voor elke variabele controleer je alle mogelijke paren van waarden in de gerelateerde domeinen (constraint checking).

- **Voorbeeld**
  Stel je hebt een boomstructuur met drie variabelen $A, B, C$ waarbij $A$ verbonden is met $B$ en $B$ met $C$. De domeinen zijn $D_A = \{1, 2\}$, $D_B = \{1, 2\}$, en $D_C = \{1, 2\}$.
  - Je controleert eerst de consistency tussen $A$ en $B$: dit kost $2^2 = 4$ controles.
  - Daarna controleer je consistency tussen $B$ en $C$: weer $4$ controles.
  - Totale complexiteit: $O(nd^2)$.

### 2.2 Consistentie

**Definitie van consistentie**
Een CSP is consistent als alle beperkingen tussen variabelen voldoen aan hun domeinen.

- **Arc Consistency**: Voor elke variabele en elke waarde in haar domein moet er een consistente waarde in het domein van de verbonden variabelen zijn.

**Belang van consistentie**
Consistentie vermindert het aantal mogelijke waarden in de domeinen, waardoor de zoekruimte kleiner wordt en het probleem efficiënter kan worden opgelost.

**Voorbeeld**

- **Inconsistentie**: Stel dat variabelen $X$ en $Y$ de beperking $X < Y$ hebben, met $D_X = \{3, 4\}$ en $D_Y = \{2, 3\}$.
  - Dit is inconsistent, want geen enkele waarde van $X$ voldoet aan $X < Y$.
- **Oplossing**: Door Arc Consistency toe te passen, wordt $D_X = \{\}$, wat aangeeft dat er geen oplossing is.
