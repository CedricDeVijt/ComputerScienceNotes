## 2.1 Voorbeeld van een Turing Machine

### Transitiespecificatie

- **Toestandsovergangen**:
  $\delta (q_0, 0) = (q_1, \sqcup , \to )$
  $\delta (q_0, 1) = (q_0, \sqcup , \to )$
  $\delta (q_1, 0) = (q_0, \sqcup , \to )$
  $\delta (q_1, 1) = (q_1, \sqcup , \to )$
  $\delta (q_0, \sqcup ) = (q_{accept}, \sqcup , \to )$
  $\delta (q_1, \sqcup ) = (q_{reject}, \sqcup , \to )$
- **Aanvaarding/Verwerping**:
  - $q_{accept}$ en $q_{reject}$ zijn eindtoestanden.

## 2.2 Uitvoering van een Turing Machine

### Voorbeeldrun met input $00010$

1. **Startconfiguratie**: $q_0 0 0 0 1 0$
2. **Stap 1**: Verwijder eerste $0$, ga naar $q_1 \to  \sqcup  q_1 0 0 1 0$
3. **Stap 2**: Verwijder volgende $0$, terug naar $q_0 \to \sqcup  \sqcup  q_0 0 1 0$
4. **Vervolgstappen**:
   - Herhaal patroon tot lege tape.
   - **Resultaat**: Machine bereikt $q_{accept}$, aanvaardt $w = 00010$.

## 2.3 Aanvaarding van Talen

### Definitie

- Een Turing Machine **aanvaardt** een woord $w$ als er een reeks configuraties $C₁ \to  C₂ \to  ... \to  C_k$ bestaat waarbij:
  1. $C₁$ is de startconfiguratie voor $w$.
  2. Elke stap volgt uit $\delta$.
  3. $C_k$ bevat $q_{accept}$.
- **Aanvaarde taal**:
  $$L(M) = \{ w \in \Sigma^* \mid M \text{ aanvaardt } w \}$$

## 2.4 Turing-Herkenbaarheid en Beslisbaarheid

### Turing-Herkenbare Talen

- Een taal is **Turing-herkenbaar** (recursief opnoembaar) als er een Turing Machine bestaat die alle woorden in de taal aanvaardt.
  - **Voorbeeld**: $A\_{TM} = \{(M, w) \mid M \text{ aanvaardt } w \}$
  - **Niet herkenbaar**: $\overline{A}_{TM}$ (complement van $A_{TM}$).

### Turing-Beslisbare Talen

- Een Turing Machine is een **beslisser** als hij stopt op **elke input**.
- **Voorbeeld**:
  $$L(M) = \{ w \in \{0,1\}^* \mid w \text{ heeft een even aantal } 0 \}$$
  - **Niet beslisbaar**: $A\_{TM}$.

## 2.5 Voorbeeld van een Beslisser: Palindrome Checker

### Machine $M_p$

1. **Stappen**:
   - Als $w$ leeg is: aanvaard.
   - Vergelijk eerste en laatste symbool:
     - Gelijk? Vervang door $\sqcup $ en herhaal.
     - Ongelijk? Verwerp.
2. **Aanvaarde taal**:
   $$L(M_p) = \{ w \in \{0,1\}^* \mid w \text{ is een palindroom} \}$$

## 2.6 Classificatie van Talen

### Overzicht

- **Reguliere talen**: Herkend door eindige automaten.
- **Contextvrije talen**: Herkend door pushdown automaten.
- **Beslisbare talen**: Turing Machines die altijd stoppen.
- **Herkenbare talen**: Turing Machines die stoppen bij aanvaarding.
- **Onherkenbare talen**: Geen TM kan ze herkennen.

## Key Points to Remember

- **Turing Machine (TM)**: Kan aanvaarden, verwerpen, of oneindig doorlopen.
- **Beslisser**: TM die **altijd stopt** (beslisbare taal).
- **Aanvaarding vs. Beslissing**:
  - Aanvaarding: TM stopt alleen bij $q_{accept}$.
  - Beslissing: TM stopt altijd, met $q_{accept}$ of $q_{reject}$.
- **Voorbeelden**:
  - $A\_{TM}$ is herkenbaar maar niet beslisbaar.
  - Palindroomchecker is een beslisser.
- **Taalhiërarchie**: Regulier ⊂ Contextvrij ⊂ Beslisbaar ⊂ Herkenbaar.
