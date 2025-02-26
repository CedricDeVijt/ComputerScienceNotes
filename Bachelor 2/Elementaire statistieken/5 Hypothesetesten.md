## 5.1 Inleiding tot Hypothesetesten

### Wat is een Hypothesetest?

- Beslissingsprobleem: kiezen tussen twee tegengestelde hypothesen.
- Nulhypothese (**$H_0$**) versus alternatieve hypothese (**$H_1$**).
- Doel: **$H_0$ verwerpen ten gunste van $H_1$**, indien er voldoende bewijs is.

### De vier stappen van een hypothesetest

1. **Hypothesen opstellen**: $H_0$ en $H_1$ formuleren.
2. **Teststatistiek definiëren**: een grootheid berekenen uit de steekproef.
3. **Beslissingsregel bepalen**: significantieniveau ($\alpha$) en criterium vaststellen.
4. **Fouten identificeren**:
   - Type I fout ($\alpha$): $H_0$ onterecht verwerpen.
   - Type II fout ($\beta$): $H_0$ onterecht behouden.

## 5.2 Hypothesetesten voor het gemiddelde

### Gemiddelde van een normale verdeling met bekende variantie

#### Tweezijdige z-test

- Hypothesen:
  - $H_0: \mu = \mu_0$
  - $H_1: \mu \neq \mu_0$
- Teststatistiek:
  $$Z = \frac{\overline X - \mu_0}{\sigma / \sqrt{n}} \sim N(0,1)$$
- Beslissingsregel:
  - $H_0$ verwerpen als Z in $[−z_{1−\alpha /2},z_{1− \alpha/2}]$

#### Eenzijdige z-test

- Hypothesen:
  - Rechsteenzijdig: $H_0: \mu \le \mu_0, H_1: \mu \gt \mu_0$
  - Linkseenzijdig: $H_0: \mu \ge \mu_0, H_1: \mu \lt \mu_0$
- Beslissingsregel:
  - $H_0$ verwerpen als $Z \gt z\left(1-\alpha\right)$ of $Z \lt -z*{1-\alpha}$.

### Gemiddelde van een normale verdeling met onbekende variantie

#### Tweezijdige t-test

- Teststatistiek:
  $$T = \frac{X - \mu*0}{S / \sqrt{n}} \sim t*{n-1}$$
- $H_0$ verwerpen als $|T| > t\_{n-1,1-\alpha/2}$.

#### Eenzijdige t-test

- $H_0$ verwerpen als $T > t*{n-1,1-\alpha}$ of $T < -t*{n-1,1-\alpha}$.

### P-waarde

- Kans om een waarde minstens zo extreem als de geobserveerde testwaarde te verkrijgen.
- $H_0$ verwerpen als $p < \alpha$.

## 5.3 Hypothesetesten voor variantie

- **Chi-kwadraat test** om varianties te vergelijken.
- Teststatistiek:
  $$X^2 = \frac{(n-1)S^2}{σ*0^2} \sim χ^2*{n-1}$$

## 5.4 Hypothesetesten voor proporties

### Benaderende test (grote steekproef)

- Teststatistiek:
  $$Z = \frac{̂p - p_0}{\sqrt{p_0(1-p_0)/n}} \sim N(0,1)$$
- $H_0$ verwerpen als $|Z| > z_{1-\alpha/2}$.

### Exacte test (kleine steekproef)

- Gebaseerd op de binomiaalverdeling.
- Directe kansberekening onder $H_0$.

## 5.5 Normaliteitsassumptie

- QQ-plot gebruiken om normaliteit te beoordelen.
- Tests zoals Shapiro-Wilk test.
- Indien niet normaal: transformaties of niet-parametrische testen overwegen.

## Key Points to Remember

- Hypothesetesten helpen bij besluitvorming onder onzekerheid.
- Een **type I fout** betekent dat een correcte nulhypothese wordt verworpen.
- Een **type II fout** betekent dat een foutieve nulhypothese niet wordt verworpen.
- **P-waarde**: hoe kleiner, hoe sterker het bewijs tegen $H_0$.
- **Z-test** wordt gebruikt als de variantie bekend is, **t-test** als de variantie onbekend is.
- **Bij kleine steekproeven** is een exacte test nodig voor proporties.
- **Normaliteitsveronderstelling** is belangrijk, vooral bij kleine steekproeven.
