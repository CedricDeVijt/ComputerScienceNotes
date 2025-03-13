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
     P(X) = \sum_{Y} P(X, Y)
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

### 5. Visualisatie op de slide\*

De slide bevat waarschijnlijk een voorbeeld van een Bayesiaans netwerk dat een 3-SAT probleem representeert, met:

- Knooppunten voor variabelen.
- Pijlen die afhankelijkheden weergeven.
- Een vraag zoals: "Wat is de kans dat een bepaalde output waar is?"

Deze structuur illustreert hoe een complex probleem in logica (3-SAT) direct correspondeert met een kansberekeningsvraag in een netwerk.

## 3 Sampeling in Bayesiaanse netwerken

### 3.1 Leg uit hoe sampling technieken werken met behulp van een voorbeeld en geef aan hoe deze sampling technieken zich verhouden tot elkaar

De vier genoemde sampling technieken worden gebruikt om het probleem van "exacte inferentie" in Bayesiaanse netwerken te omzeilen. Bij exacte inferentie wordt geprobeerd om precies de waarschijnlijkheidsverdeling van de variabelen in een netwerk te berekenen, wat vaak erg complex en tijdrovend is. Daarom worden deze sampling technieken gebruikt om een benadering van de waarschijnlijkheden te krijgen zonder de volledige berekeningen.

#### 1. **Prior Sampling**

**Hoe het werkt**:

- **Prior Sampling** genereert willekeurige monsters uit de prior distributie van een netwerk. Dit betekent dat je samples trekt zonder rekening te houden met de waarnemingen of bewijzen (evidence) die je hebt.
- **Voorbeeld**:
  Stel je een eenvoudig Bayesiaans netwerk voor met twee variabelen: `A` en `B`. De prior distributies van `A` en `B` kunnen bijvoorbeeld zijn:

  - P(A = true) = 0.6, P(A = false) = 0.4
  - P(B = true) = 0.7, P(B = false) = 0.3

  Als je prior samples genereert, trek je bijvoorbeeld 10.000 willekeurige monsters voor de waarden van `A` en `B` op basis van deze prior distributies, zonder te kijken naar bewijs zoals waarnemingen van de variabelen.

- **Nadeel**: Het trekt geen samples die rekening houden met bewijs of waarnemingen, wat betekent dat het mogelijk samples genereert die inconsistent zijn met wat we weten (bewijzen). Hierdoor is het minder efficiënt wanneer je al bewijs hebt.

#### 2. **Rejection Sampling**

**Hoe het werkt**:

- **Rejection Sampling** genereert eerst een sample van de prior distributie (zoals bij prior sampling). Vervolgens wordt elk sample "afgewezen" als het inconsistent is met het bewijs. Dat wil zeggen, als een sample niet voldoet aan de waarnemingen die je hebt (bijvoorbeeld je weet dat B waar is), dan wordt dat sample verworpen.
- **Voorbeeld**:
  Stel dat je weet dat `B = true`. Je trekt een sample voor `A` en `B` uit de prior distributie. Als het sample `B = false` oplevert, wordt het afgewezen. Alleen samples waarbij `B = true` behouden blijven.

- **Nadeel**: Rejection sampling kan inefficiënt zijn, vooral als de waarnemingen veel bewijs bevatten dat de samples sterk beperkt. Het kan veel samples verwerpen, waardoor de methode traag wordt.

#### 3. **Likelihood Weighting**

**Hoe het werkt**:

- **Likelihood Weighting** werkt door samples te trekken uit de prior distributie, maar met gewichten die rekening houden met het bewijs. In plaats van samples te verwerpen zoals bij rejection sampling, worden ze gewogen afhankelijk van hoe waarschijnlijk het bewijs is, gegeven de getrokken sample.
- **Voorbeeld**:
  Stel dat je weer het netwerk hebt met `A` en `B`, en je weet dat `B = true`. In plaats van samples met `B = false` af te wijzen, geef je ze een gewicht van 0 als ze niet overeenkomen met `B = true`. Samples waarbij `B = true` krijgen een gewicht gebaseerd op de waarschijnlijkheid van de waarneming (bijvoorbeeld P(B = true | sample)).

  Dit resulteert in een set samples die een gewogen representatie van de distributie is, aangepast voor het bewijs.

- **Nadeel**: Hoewel het efficiënt is in vergelijking met rejection sampling, kan de kwaliteit van de schatting afhankelijk zijn van de keuze van de gewichten.

#### 4. **Gibbs Sampling**

**Hoe het werkt**:

- **Gibbs Sampling** is een iteratieve techniek waarbij je de waarde van elke variabele in het netwerk één voor één resampled, waarbij je altijd de huidige waarden van de andere variabelen vastzet en alleen de waarde van de gekozen variabele aanpast, gebaseerd op de conditionele distributie van die variabele gegeven de andere variabelen.
- **Voorbeeld**:
  Stel je hebt een netwerk met de variabelen `A` en `B`. Bij Gibbs sampling begin je met willekeurige waarden voor `A` en `B`. Vervolgens:

  - Je berekent de conditionele distributie van `A` gegeven `B` en samplet een nieuwe waarde voor `A`.
  - Daarna sample je de waarde van `B` gegeven de nieuwe waarde van `A`.
  - Dit herhaal je iteratief totdat je een set van samples hebt die de volledige distributie van de variabelen reflecteert.

- **Nadeel**: Het kan tijd kosten voordat de samples goed gemengd zijn en representatief zijn voor de volledige distributie (burn-in periode). Het kan ook traag zijn in netwerken met veel variabelen, vooral als de conditionele distributies complex zijn.

#### Vergelijking van de technieken

| Techniek                 | Hoe het werkt                                                                             | Voordelen                                  | Nadelen                                            |
| ------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------ | -------------------------------------------------- |
| **Prior Sampling**       | Samples trekken uit de prior distributie zonder bewijs                                    | Simpel en makkelijk te implementeren       | Inefficiënt bij bewijs, kan veel tijd kosten       |
| **Rejection Sampling**   | Samples trekken uit prior, maar samples die niet met bewijs overeenkomen worden verworpen | Nauwkeurige samples, eenvoudig concept     | Kan veel samples verwerpen, traag bij sterk bewijs |
| **Likelihood Weighting** | Samples trekken uit prior en gewichten aanpassen op basis van bewijs                      | Efficiënter dan rejection sampling         | Kan afhangen van juiste gewichtenschatting         |
| **Gibbs Sampling**       | Iteratief resamplen van variabelen, één voor één, gegeven andere variabelen               | Goede convergentie met voldoende iteraties | Kan langzaam zijn, vooral voor grote netwerken     |

**Conclusie**:

- **Prior Sampling** is snel, maar negeert bewijs, en kan onbetrouwbare samples opleveren.
- **Rejection Sampling** kan preciesere resultaten opleveren, maar is niet efficiënt als veel bewijs beschikbaar is.
- **Likelihood Weighting** is efficiënter dan rejection sampling, maar kan onbetrouwbaar zijn bij slecht gekozen gewichten.
- **Gibbs Sampling** is krachtig en vaak effectief, vooral als je iteraties voldoende lang doorgaan, maar het kan traag zijn in complexe netwerken.

### 3.2 Oplossen van Bayesiaanse netwerken met sampling technieken

Gibbs sampling werkt door de waarde van $D$ herhaaldelijk te updaten op basis van de voorwaardelijke verdelingen van de variabelen in het Bayesiaans netwerk, gegeven de waarden van $C = +$ en $A = -$.

1. Begin met willekeurige waarden voor $D$, $A$ en $C$, waarbij $A = -$ en $C = +$.
2. Update $D$ op basis van de voorwaardelijke verdeling $P(D | A, C)$.
3. Update $A$ op basis van $P(A | D, C)$.
4. Update $C$ op basis van $P(C | D, A)$.
5. Herhaal dit proces veelvuldig (bijvoorbeeld duizenden keren).
6. Na genoeg iteraties, bereken het gemiddelde of tel hoe vaak elke waarde van $D$ voorkomt. Dit geeft je een benadering van $P(D | C=+, A=-)$.

Het resultaat is een steekproef uit de voorwaardelijke verdeling van $D$.
