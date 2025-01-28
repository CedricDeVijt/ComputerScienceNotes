## 1.1 Inleiding tot Berekeningsmodellen

- **Eindige automaten**: Beperkt geheugen; modelleert reguliere talen.
- **Pushdown automaten**: Oneindig geheugen als stack; modelleert contextvrije talen.
- **Turing Machines (TM)**: Universeel model voor algoritmen; formaliseert alle bekende berekeningen (Church-Turingthese: _Algoritme = TM_).

## 1.2 Definitie van een Deterministische Turing Machine

Een TM bestaat uit:

- **Eindige toestanden (Q)**: Inclusief starttoestand $q_0$, aanvaardings- ($q_{accept}$) en verwerpingstoestanden ($q_{reject}$).
- **Tape**:
  - Oneindig in beide richtingen.
  - Bevat symbolen uit het tape-alfabet $\Gamma$, inclusief input-alfabet $\Sigma$, lege symbool $\cup$, en markeringen $\vdash$ (startpositie) en $\bot$.
- **Lees/schrijfkop**: Beweegt links, rechts, of blijft staan.
- **Transitiefunctie $\delta$**:
  $$
  \delta: Q \times \Gamma \rightarrow Q \times \Gamma \times \{\leftarrow, \square, \rightarrow\}
  $$
  - Voor $\delta(q, a) = (q', b, X)$:
    - Schrijf $b$, verander naar toestand $q'$, beweeg volgens $X$.

## 1.3 Configuraties en Berekeningen

### Configuratie Representatie

- **Notatie**: $u \, q \, v$, waarbij:
  - $u$: Tapeinhoud links van de kop.
  - $q$: Huidige toestand.
  - $v$: Tapeinhoud vanaf de kop.
- **Startconfiguratie**: $\vdash q_0 w$ (input $w$ op posities 1 tot $n$, overige posities $\cup$).

### Overgangsregels

- Voor $u a q_i b v$:
  - **Beweging links**: $u q_j a c v$ als $\delta(q_i, b) = (q_j, c, \leftarrow)$.
  - **Beweging rechts**: $u a c q_j v$ als $\delta(q_i, b) = (q_j, c, \rightarrow)$.
  - **Blijven staan**: $u a q_j c v$ als $\delta(q_i, b) = (q_j, c, \square)$.

## 1.4 Aanvaarding van Talen

- **Aanvaardingsvoorwaarde**: TM bereikt $q_{accept}$.
- **Verwerping**: TM bereikt $q_{reject}$.
- **Taal van TM $M$**:
  $$
  L(M) = \{ w \in \Sigma^* \mid M \text{ aanvaardt } w \}
  $$
- **Turing-herkenbaarheid**: Een taal $L$ is Turing-herkenbaar als er een TM bestaat die $L$ aanvaardt.
  **Voorbeeld**: $A_{TM} = \{ (M, w) \mid M \text{ aanvaardt } w \}$ is herkenbaar, maar zijn complement niet.

## 1.5 Voorbeeld: TM voor Even Aantal Nullen

### Specificatie

- **Toestanden**: $Q = \{ q_0, q_1, q_{accept}, q_{reject} \}$
- **Transities**:
  - $\delta(q_0, 0) = (q_1, \cup, \rightarrow)$
  - $\delta(q_0, 1) = (q_0, \cup, \rightarrow)$
  - $\delta(q_1, 0) = (q_0, \cup, \rightarrow)$
  - $\delta(q_1, 1) = (q_1, \cup, \rightarrow)$
  - $\delta(q_0, \cup) = (q_{accept}, \cup, \rightarrow)$
  - $\delta(q_1, \cup) = (q_{reject}, \cup, \rightarrow)$

### Uitvoering op Input $w = 00010$

1. Start: $\vdash q_0 00010$
2. Stappen:
   - $q_0 \rightarrow q_1$ (na eerste 0).
   - $q_1 \rightarrow q_0$ (na tweede 0).
   - Herhaal tot einde tape; eindigt in $q_{accept}$.

## 1.6 Belangrijke Concepten

### Church-Turingthese

- Elke algoritmisch oplosbaar probleem kan door een TM worden geïmplementeerd.

### Halting Probleem

- $\tilde{A}_{TM}$ (complement van $A_{TM}$) is niet Turing-herkenbaar.

### Tapesymbolen en Beperkingen

- $\vdash$ kan niet overschreven worden, behalve op positie 0.
- Beweging links van $\vdash$ is onmogelijk.

## Key Points to Remember

- **Componenten van een TM**: Eindige toestanden, oneindige tape, transitiefunctie.
- **Church-Turingthese**: TM's modelleren alle algoritmen.
- **Configuraties**: Worden gerepresenteerd als $u \, q \, v$.
- **Aanvaarding**: Input wordt aanvaard als $q_{accept}$ bereikt wordt.
- **Turing-herkenbaarheid**: Vereist dat de TM stopt voor aanvaarde inputs, maar niet noodzakelijk voor verworpen inputs.
- **Voorbeeld-TM**: Checkt even aantal nullen door toestanden te wisselen bij elke 0.
- **Halting Probleem**: Toont de beperkingen van TM's (niet alle talen zijn beslisbaar).
