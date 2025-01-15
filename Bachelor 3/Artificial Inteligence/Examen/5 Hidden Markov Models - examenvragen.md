## 1. Bereken de kans op een bepaalde observatie bij een gegeven HMM

### Stappenplan om een kans te berekenen in een HMM

1. **Definieer de elementen van het HMM**:

   - Stel de toestanden (Γ) vast.
   - Stel de observaties (Ω) vast.
   - Bepaal de startkansen ($\pi$), de transitiekansen (A), en de emissiekansen (B).

2. **Bepaal de observatiereeks**:

   - Noteer de reeks observaties waarvoor de kans berekend moet worden.

3. **Gebruik het Forward-algoritme**:

   - Initialisatie: Bereken de initiële waarschijnlijkheid van elke toestand gebaseerd op de eerste observatie.
     $$α_1(i) = \pi_i B_i(O_1)$$
   - Recursie: Bereken de cumulatieve waarschijnlijkheid voor elke toestand en iedere volgende observatie:
     $$αt(j) = \sum\limits_{i} α{t-1}(i) A*{ij} B_j(O_t)$$
   - Terminatie: Sommeer de waarden voor de laatste observatie:
     $$P(O|\lambda) = \sum\limits_{i} α_T(i)$$

4. **Interpreteer de uitkomst**:
   - De resulterende waarde is de kans op de gegeven observatiereeks, gegeven het HMM.

## 2. Particle filtering in HMM

### Hoe werkt particle filtering in een HMM?

Particle filtering is een techniek om een benadering te maken van de posterior distributie over toestanden in een dynamisch systeem. Het werkt als volgt:

1. **Initialisatie**:

   - Genereer een set van $N$ deeltjes (particles), elk met een gewicht $w_i$. Begin met een uniforme verdeling of de startkansen van het HMM.

2. **Voorspelling**:

   - Gebruik de transitiekansen om de volgende toestand van elk deeltje te simuleren.

3. **Bijwerken van gewichten**:

   - Bereken de waarschijnlijkheid van de observatie voor elk deeltje en werk het gewicht $w_i$ bij:
     $$w_i = w_i \cdot B(O_t|s_i)$$
   - Normaliseer de gewichten.

4. **Resampling**:

   - Selecteer $N$ deeltjes opnieuw gebaseerd op hun gewichten (deeltjes met een hoger gewicht hebben meer kans om geselecteerd te worden).

5. **Itereren**:

   - Herhaal stappen 2-4 voor iedere volgende observatie.

6. **Resultaat**:
   - De resulterende deeltjes en hun gewichten geven een benadering van de posterior distributie over toestanden.

## 3. Algoritmes

### 3.1 Viterbi

Het Viterbi-algoritme wordt gebruikt om de meest waarschijnlijke volgorde van toestanden te bepalen, gegeven een observatiereeks.

**Werking**:

1. **Initialisatie**:

   - Bereken de waarschijnlijkheid van de eerste observatie in elke toestand:
     $$\delta_1(i) = \pi_i B_i(O_1)$$
   - Sla de vorige toestanden op.

2. **Recursie**:

   - Voor iedere observatie en toestand bereken je de maximale waarschijnlijkheid:
     $$\delta*t(j) = \max*{i} (\delta*{t-1}(i) A*{ij}) B_j(O_t)$$
   - Houd bij welke toestand de maximale waarde geeft.

3. **Backtracking**:

   - Begin bij de laatste tijdstap en loop terug langs de opgeslagen toestanden om de meest waarschijnlijke volgorde te reconstrueren.

4. **Uitkomst**:
   - De resulterende toestandsreeks is de meest waarschijnlijke sequentie.

### 3.2 Forward

Het Forward-algoritme berekent de waarschijnlijkheid van een observatiereeks, zoals beschreven in sectie 1.

**Doel**:

- Het algoritme bepaalt $P(O|\lambda)$, de kans op een observatiereeks $O$.

**Werking**:

1. **Initialisatie**:

   - Bereken $α_1(i) = \pi_i B_i(O_1)$.

2. **Recursie**:

   - Voor iedere tijdstap en toestand:
     $$α*t(j) = \sum*{i} α*{t-1}(i) A*{ij} B_j(O_t)$$

3. **Terminatie**:
   - Sommeer de waarden voor de laatste tijdstap:
     $$P(O|\lambda) = \sum\_{i} α_T(i)$$

### 3.3 Backward

Het Backward-algoritme wordt gebruikt om de waarschijnlijkheid van de resterende observaties te berekenen vanaf een bepaald tijdstip.

**Werking**:

1. **Initialisatie**:

   - Zet $β_T(i) = 1$ voor alle toestanden bij de laatste observatie.

2. **Recursie**:

   - Bereken $β*t(i)$ voor eerdere tijdstappen:
     $$β_t(i) = \sum*{j} A*{ij} B_j(O*{t+1}) β\_{t+1}(j)$$

3. **Resultaat**:
   - Combineer met Forward om posterior kansen te berekenen:
     $$P(s_t|O,\lambda) \propto α_t(i) β_t(i)$$
