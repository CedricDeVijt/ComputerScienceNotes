## 3.1 Inleiding tot Computationele Complexiteit

### Definitie en Middelen

- Computationele complexiteit meet de benodigde middelen (zoals tijd, geheugen, randomiteit) om een probleem op te lossen.
- **Tijdscomplexiteit**: Focus op het aantal stappen dat een algoritme nodig heeft om een input van lengte $n$ te verwerken.

### Tijdscomplexiteit van een Algoritme

- Een **Turingmachine (TM)** stopt op elke input.
- **Stap van een TM**: Uitvoeren van één instructie uit de transitiefunctie.
- **Worst-case tijdscomplexiteit**:
  $$t_M(n) = \max\{ \textit{time}\_M(w) \mid w \in \Sigma^* \text{ en } |w| = n \}$$
  Hierbij is $|w|$ de lengte van de input.

## 3.2 Analyse van een Voorbeeld-Turingmachine (Mp)

### Beschrijving van Mp

De TM $M_p$ werkt als volgt op een inputwoord $w$:

1. Als $w$ leeg is, aanvaard (1 stap).
2. Overschrijf het eerste symbool (0/1) met "LJ" en ga naar het einde van het woord (max $n$ stappen).
3. Overschrijf het laatste symbool indien het overeenkomt met het eerste (1 stap).
4. Verwerp bij verschillende symbolen (1 stap).
5. Controleer of links van de kop "LJ" staat; zo niet, ga terug naar het vorige "LJ" (max $n$ stappen).
6. Herhaal dit proces (max $\frac{n}{2}$ iteraties).

### Stapsgewijze Tijdsanalyse

- **Stap 1**: 1 stap.
- **Stap 2**: $n$ stappen.
- **Stap 3**: 1 stap.
- **Stap 4**: 1 stap.
- **Stap 5**: $n$ stappen per iteratie.
- **Stap 6**: Maximaal $\frac{n}{2}$ herhalingen.

### Totale Tijdscomplexiteit

$$
\text{Totaal} = \frac{n}{2} \times (2n + 2) = n^2 + n
$$

- Dominante term: $O(n^2)$.

## 3.3 Asymptotische Analyse

### Doel en Belang

- Exacte stappen zijn minder relevant; focus ligt op **groei** van complexiteit bij toenemende inputlengte.
- Analyseer het asymptotisch gedrag (bijv. $n \rightarrow \infty$) om algoritmen te vergelijken.

## Key Points to Remember

- **Worst-case complexiteit**: Meet de maximale tijd voor inputs van lengte $n$.
- **Turingmachine-stappen**: Eén transitie-instructie telt als één stap.
- **Voorbeeld $M_p$**:
  - Tijdscomplexiteit is kwadratisch ($O(n^2)$) door herhaaldelijk traverseren van de input.
- **Asymptotische analyse**: Richt zich op de groeisnelheid van complexiteit, niet op exacte getallen.
- **Sleutelformules**:
  - $t_M(n) = \max\{ \textit{time}\_M(w) \}$
  - Totale stappen voor $M_p$: $\frac{n}{2}(2n + 2)$.
