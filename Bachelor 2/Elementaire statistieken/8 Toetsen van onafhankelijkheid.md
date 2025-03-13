## 8.1 Onafhankelijkheid van Discrete Variabelen

### Contingentietabel en Theoretische Frequenties

- **Steekproef**: Paarsgewijze waarnemingen $\{(X_1, Y_1), \ldots, (X_n, Y_n)\}$ voor discrete variabelen $X$ (met $r$ categorieën) en $Y$ (met $k$ categorieën).
- **Waargenomen frequenties**: $N_{lj} =$ aantal waarnemingen met $X = l$ en $Y = j$.
- **Marginale frequenties**:
  - $N*{l.} = \sum_j N*{lj}$ (rijtotalen)
  - $N*{.j} = \sum_l N*{lj}$ (kolomtotalen).
- **Theoretische frequenties onder $H_0$** (onafhankelijkheid):
  $$
  \hat{E}_{lj} = \frac{N_{l.} \cdot N_{.j}}{n}
  $$

### Chi-Kwadraat Toets

- **Teststatistiek**:
  $$
  \chi^2 = \sum*{l=1}^r \sum*{j=1}^k \frac{(N*{lj} - \hat{E}*{lj})^2}{\hat{E}_{lj}}
  $$
- **Vrijheidsgraden**:
  $$
  (r-1)(k-1)
  $$
- **Voorwaarde**: Alle $\hat{E}_{lj} \geq 5$. Zo niet, hergroepeer categorieën.
- **Besluitingsregel**: Verwerp $H*0$ als $\chi^2 > \chi^2*{(r-1)(k-1), 1-\alpha}$.

#### Voorbeeld: Alcoholgebruik en Examenresultaten

- **Geobserveerde tabel**:

  |            | Niet Geslaagd | Geslaagd | Totaal |
  | ---------- | ------------- | -------- | ------ |
  | Regelmatig | 70            | 35       | 105    |
  | Soms       | 331           | 377      | 708    |
  | Nooit      | 39            | 18       | 57     |
  | **Totaal** | 440           | 430      | 870    |

- **Berekende $\chi^2 = 22.33$** met 2 vrijheidsgraden. Verwerp $H_0$ ($\alpha = 1\%$, kritieke waarde = 9.21).

## 8.2 Onafhankelijkheid van Continue Variabelen

### Covariantie en Correlatie

- **Covariantie**:
  $$
  S*{XY} = \frac{1}{n-1} \sum*{i=1}^n (X_i - \overline{X})(Y_i - \overline{Y})
  $$
- **Pearson Correlatiecoëfficiënt**:
  $$
  R*{XY} = \frac{S*{XY}}{\sqrt{S_X^2 S_Y^2}}
  $$
  - Waarden: $-1 \leq R_{XY} \leq 1$.
  - Onafhankelijkheid $\Rightarrow R_{XY} = 0$, maar omgekeerd niet altijd waar.

### Hypothesetoets voor Correlatie

- **Hypothesen**:
  - $H_0: \text{Corr}[X, Y] = 0$
  - $H_1: \text{Corr}[X, Y] \neq 0$ (tweezijdig) of $H_1: \text{Corr}[X, Y] >/< 0$ (eenzijdig).
- **Teststatistiek**:
  $$
  T = \frac{R*{XY}}{\sqrt{\frac{1 - R*{XY}^2}{n - 2}}} \sim t_{n-2} \quad \text{onder } H_0
  $$
- **Aanvaardingsgebied**:
  - Tweezijdig: $[-t_{n-2, 1-\alpha/2}, t_{n-2, 1-\alpha/2}]$
  - Eenzijdig: $[-\infty, t_{n-2, 1-\alpha}]$ of $[-t_{n-2, 1-\alpha}, \infty)$.

#### Voorbeeld: Gewichtstooname Moeder en Pasgeborene

- **Steekproef**: $n = 30$, $r_{xy} = 0.47$.
- **Teststatistiek**: $T = 2.818$.
- **Eenzijdig kritieke waarde**: $t_{28, 0.95} = 1.7011$. Verwerp $H_0$ ($\alpha = 5\%$).

## 8.3 Belangrijke Opmerkingen

### Chi-Kwadraat Toets

- **Invariantie**: Resultaat blijft hetzelfde bij permutatie van $X$ en $Y$ of hercodering.
- **2×2 Tabellen**: Positieve/negatieve relaties kunnen worden geïdentificeerd via afwijkingen van verwachte frequenties.
- **Continue Variabelen**: Groepeer in klassen voor toepassing van chi-kwadraat.

### Correlatie

- **Lineaire Relaties**: $R_{XY} = \pm 1$ wijst op perfecte lineaire samenhang.
- **Niet-lineaire Relaties**: Correlatie 0 sluit niet-lineaire afhankelijkheid niet uit (bijv. $Y = X^2$).

## 8.4 Sleutelpunten

- **Chi-Kwadraat Toets**:
  - Gebruikt voor discrete variabelen.
  - Vrijheidsgraden = $(r-1)(k-1)$.
  - Theoretische frequenties moeten ≥5 zijn.
- **Pearson Correlatie**:
  - Meet lineaire samenhang; $R_{XY} = 0$ betekent geen lineair verband.
  - Toets via $t$-verdeling met $n-2$ vrijheidsgraden.
- **Interpretatie**:
  - Significantie van $\chi^2$ of $T$ bepaalt verwerping $H_0$.
  - Correlatie ≠ causaliteit.
- **Praktische Voorbeelden**:
  - Alcoholgebruik vs. examenresultaten: sterke afhankelijkheid.
  - Gewichtstooname moeder vs. pasgeborene: positieve lineaire relatie.
