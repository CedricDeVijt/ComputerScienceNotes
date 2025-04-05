## 7.1 Chi-Squared Test voor Discrete Verdelingen

### Theoretische Achtergrond

- **Doel**: Testen of waarnemingen uit een gegeven discrete verdeling komen.
- **Hypothese**:
  $H_0$: De steekproef volgt de theoretische verdeling met kansen $\{p_1, \ldots, p_k\}$.
  $H_1$: De steekproef volgt de theoretische verdeling niet.
- **Frequenties**:
  - Waargenomen frequenties $N_j$ (aantal waarnemingen $z_j$).
  - Theoretische frequenties $np_j$ (verwacht aantal onder $H_0$).

### Teststatistiek

$$
\chi^2 = \sum_{j=1}^k \frac{(N_j - np_j)^2}{np_j}
$$

- **Verdeling**: Benaderend $\chi^2_{k-1}$ (aantal vrijheidsgraden = $k-1$).
- **Aanvaardingsgebied**: $[0, \chi^2_{k-1; 1-\alpha}]$.

### Voorbeeld: Uniforme Verdeling van Bibliotheekbezoek

- **Gegevens**:

  | Dag | ma | di | woe | do | vrij | zat |
  |-----|-----|-----|------|-----|-------|------|
  | $n_j$ | 26 | 32 | 23 | 29 | 34 | 41 |

  $n = 185$, $p_j = \frac{1}{6}$, $np_j = 30.833$.

- **Berekening**:
  $$
  \chi^2 = \frac{1}{30.833} \left(23.361 + 1.361 + \ldots + 103.361\right) = 6.578
  $$
- **Conclusie**:
  $\chi^2_{5; 0.95} = 11.070$. Aangezien $6.578 < 11.070$, wordt $H_0$ aanvaard.

## 7.2 Chi-Squared Test voor Continue Verdelingen

### Methodologie

- **Stappen**:
  1. Verdeel de data in $k$ klassen.
  2. Bereken theoretische kansen $p_j$ en frequenties $np_j$.
  3. Combineer klassen indien $np_j < 5$.
  4. Gebruik dezelfde $\chi^2$-formule als bij discrete verdelingen.
- **Vrijheidsgraden**:
  $\chi^2_{k-v-1}$ als $v$ parameters geschat zijn.

### Voorbeeld: Normale Verdeling van Snelheidsmetingen

- **Gegevens**: 300 snelheden, ingedeeld in 10 klassen.
- **Parameters**:
  $\hat{\mu} = 68.22$, $\hat{\sigma} = 8.91$.
- **Theoretische kansen**: Gebaseerd op $N(68.22, 79.36)$.
- **Teststatistiek**:
  $\chi^2 = 21.64$, $\chi^2_{6; 0.95} = 12.592$.
- **Conclusie**: $21.64 > 12.592$, dus $H_0$ wordt verworpen.

## 7.3 Kolmogorov-Smirnov Test

### Theoretische Achtergrond

- **Doel**: Testen of een continue steekproef uit een specifieke verdeling $P$ komt.
- **Teststatistiek**:
  $$
  D = \sup_x |\hat{F}_n(x) - F_P(x)|
  $$
  waarbij $\hat{F}_n(x)$ de empirische verdelingsfunctie is.
- **Voordelen**: Exacte test, geen vereisten voor steekproefgrootte.

## 7.4 Belangrijke Opmerkingen

1. **Voorwaarden voor $\chi^2$-test**:
   - Theoretische frequenties $np_j \geq 5$.
   - Combineer klassen indien nodig.
2. **Vrijheidsgraden**:
   - $k-1$ voor discrete verdelingen.
   - $k-v-1$ indien $v$ parameters geschat zijn.
3. **Kolmogorov-Smirnov**:
   - Geschikt voor kleine steekproeven.
   - Vergelijkt empirische en theoretische verdelingsfuncties.

---

## Key Points to Remember

- **Chi-Squared Test**:
  - Gebruikt voor discrete en continue verdelingen.
  - Teststatistiek: $\sum \frac{(N_j - np_j)^2}{np_j} \sim \chi^2$.
  - Vrijheidsgraden hangen af van geschatte parameters.
- **Kolmogorov-Smirnov**:
  - Exacte test, gebaseerd op maximale afwijking tussen verdelingsfuncties.
- **Voorwaarden**:
  - Theoretische frequenties $\geq 5$ voor $\chi^2$-test.
  - Combineer klassen indien nodig.
- **Voorbeelden**:
  - Uniforme verdeling: $H_0$ aanvaard.
  - Normale verdeling: $H_0$ verworpen.
