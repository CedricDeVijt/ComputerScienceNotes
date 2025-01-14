## 1 Onafhankelijkheid bepalen gegeven een Bayesiaans netwerk

#### Stappenplan:

1. **Identificeer de structuur van het netwerk:**

   - Teken het netwerk (als het niet al gegeven is).
   - Noteer de knopen (variabelen) en de pijlen (afhankelijkheden).

2. **Gebruik de begrippen van directe afhankelijkheid en d-separatie:**

   - Twee knopen zijn direct afhankelijk als er een directe pijlpunt tussen hen is.
   - Gebruik d-separatie om te bepalen of twee variabelen afhankelijk of onafhankelijk zijn, gegeven een set condities. Controleer:
     - **Directe afhankelijkheid**: Een variabele is afhankelijk van zijn ouder(s) en kind(eren).
     - **Conditionele onafhankelijkheid**: Variabelen kunnen onafhankelijk worden als je conditioneert op een derde variabele (d-separatie):
       - **Chain structure (X → Z → Y)**: $X$ en $Y$ zijn afhankelijk tenzij $Z$ gegeven is.
       - **Common cause (X ← Z → Y)**: $X$ en $Y$ zijn afhankelijk tenzij $Z$ gegeven is.
       - **Collider (X → Z ← Y)**: $X$ en $Y$ zijn onafhankelijk tenzij $Z$ (of een afstammeling van $Z$) gegeven is.

3. **Formuleer de onafhankelijkheidsrelaties:**

   - Noteer welke knopen onafhankelijk zijn en onder welke condities. Gebruik notatie zoals $X \perp Y \mid Z$ (X is onafhankelijk van Y gegeven Z).

4. **Controleer tegen de structuur en condities:**
   - Bevestig de d-separatie regels door de pijlen in het netwerk te volgen.

## 2 Gegeven een Bayesiaans netwerk, bereken de kans op een bepaalde gebeurtenis

#### Stappenplan:

1. **Schrijf de factorisatie van de joint probability distribution (JPD):**

   - Een Bayesiaans netwerk factoriseert de JPD in termen van de conditional probabilities:
     $$
     P(X*1, X_2, \dots, X_n) = \prod*{i=1}^n P(X_i \mid \text{Parents}(X_i))
     $$

2. **Identificeer de relevante variabelen:**

   - Bepaal de variabele(s) waarvan je de kans wilt berekenen, en welke condities (indien aanwezig) gegeven zijn.

3. **Gebruik marginalisatie:**

   - Als je een marginale kans wilt berekenen, som of integreer je over de niet-relevante variabelen:
     $$
     P(X) = \sum\_{Y} P(X, Y)
     $$

4. **Gebruik conditionele kansregels:**

   - Als een kans wordt gegeven in de vorm $P(A \mid B)$, gebruik:
     $$
     P(A \mid B) = \frac{P(A, B)}{P(B)}
     $$

5. **Voer inferentie uit met exacte methodes:**

   - **Handmatig**:
     - Gebruik de factorisatie van het netwerk en werk stapsgewijs.
   - **Met algoritmes**:
     - **Variable elimination**: Elimineer variabelen door overbodige variabelen samen te voegen (marginalisatie).
     - **Belief propagation**: Gebruik distributie-updates langs de randen van het netwerk.

6. **Voor complexe netwerken gebruik numerieke methoden:**
   - **Monte Carlo-sampling**: Gebruik technieken zoals Gibbs sampling of Rejection sampling om kanswaardes te benaderen.

## 3 Tijdscomplexiteit van Bayesiaanse netwerken

Het bewijs dat inference in Bayesiaanse netwerken NP-hard is, maakt gebruik van een reductie vanuit een bekend NP-volledig probleem, meestal het **3-SAT probleem**. De slide die je noemt, bevat waarschijnlijk een visualisatie of uitleg over hoe dit bewijs wordt uitgevoerd. Hier is een eenvoudige uitleg van hoe het bewijs doorgaans wordt opgebouwd:

### 1. Wat betekent inference in een Bayesiaans netwerk?

Inference in een Bayesiaans netwerk betekent dat we de waarschijnlijkheid van een bepaalde gebeurtenis berekenen, gegeven wat we weten over andere gebeurtenissen. Bijvoorbeeld: "Wat is de kans dat een ziekte aanwezig is, gegeven bepaalde symptomen?" Dit komt neer op het berekenen van marginale waarschijnlijkheden of conditionele waarschijnlijkheden.

### 2. Waarom NP-hard?

NP-hard betekent dat een probleem ten minste even moeilijk is als de moeilijkste problemen in NP. Dit wordt bewezen door te laten zien dat een bekend NP-volledig probleem kan worden opgelost door het om te zetten naar een inference-probleem in een Bayesiaans netwerk.

### 3. Reductie vanuit 3-SAT:

Het bewijs laat zien dat we elk willekeurig 3-SAT probleem kunnen omzetten in een inference-vraag binnen een Bayesiaans netwerk.

- **3-SAT probleem**: Dit is een logische formule in conjunctieve normale vorm (CNF) waarin elke clausule precies drie literalen bevat. De vraag is of er een toekenning van `waar/onwaar` bestaat aan de variabelen zodat de formule waar wordt.

- **Omzetting naar een Bayesiaans netwerk**:
  1. **Variabelen modelleren**: Voor elke variabele in de 3-SAT-formule wordt een corresponderend knooppunt in het Bayesiaanse netwerk gemaakt.
  2. **Clausules modelleren**: Elke clausule in de formule wordt gerepresenteerd door een set afhankelijkheden en condities tussen de variabelen in het netwerk.
  3. **Inference stellen**: De vraag of de formule kan worden opgelost (satisfiability) wordt herformuleerd als een kansberekening in het netwerk. Bijvoorbeeld: "Wat is de kans dat een specifieke configuratie van variabelen waar is?"

### 4. Waarom NP-hard?

De omzetting laat zien dat als je een efficiënte methode hebt om inference in een Bayesiaans netwerk op te lossen, je deze kunt gebruiken om ook elk 3-SAT probleem efficiënt op te lossen. Aangezien 3-SAT NP-volledig is, en inference dus minstens even moeilijk, wordt geconcludeerd dat inference in Bayesiaanse netwerken NP-hard is.

### 5. Visualisatie op de slide*

De slide bevat waarschijnlijk een voorbeeld van een Bayesiaans netwerk dat een 3-SAT probleem representeert, met:

- Knooppunten voor variabelen.
- Pijlen die afhankelijkheden weergeven.
- Een vraag zoals: "Wat is de kans dat een bepaalde output waar is?"

Deze structuur illustreert hoe een complex probleem in logica (3-SAT) direct correspondeert met een kansberekeningsvraag in een netwerk.

## 2 Sampeling in Bayesiaanse netwerken
