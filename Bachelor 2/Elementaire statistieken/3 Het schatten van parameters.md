## 3.1 Het Steekproefgemiddelde als Schatter

### Concept en Betrouwbaarheid

- Het steekproefgemiddelde $\overline{X}_n$ is een schatter voor het populatiegemiddelde $\mu$.
- Het is afhankelijk van de gekozen steekproef en varieert tussen verschillende steekproeven.
- **Notatie**:
  - $\overline{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$ (stochastische veranderlijke).
  - $\overline{x}_n = \frac{1}{n} \sum_{i=1}^n x_i$ (geobserveerde waarde).

### Verdeling van het Steekproefgemiddelde

- **Verwachtingswaarde**:
  $E[\overline{X}_n] = \mu$ (zuivere schatter).
- **Variantie**:
  $\text{Var}(\overline{X}_n) = \frac{\sigma^2}{n}$, waarbij $\sigma^2$ de populatievariantie is.
- De spreiding van $\overline{X}_n$ neemt af bij grotere steekproeven.
- **Normaliteit**:
  - Voor normaal verdeelde populaties: $\overline{X}_n \sim N\left(\mu, \frac{\sigma^2}{n}\right)$.
  - Voor niet-normale populaties: benadering via centrale limietstelling (CLT).

### Centrale Limietstelling (CLT)

- Als $X_1, X_2, \dots, X_n$ i.i.d. zijn met $E[X_i] = \mu$ en $\text{Var}(X_i) = \sigma^2$, dan geldt voor grote $n$:
  $$
  \sqrt{n} \left( \frac{\overline{X}_n - \mu}{\sigma} \right) \xrightarrow{D} N(0, 1).
  $$
- **Conclusie**:
  $\overline{X}_n \approx N\left(\mu, \frac{\sigma^2}{n}\right)$, ongeacht de oorspronkelijke verdeling.

## 3.2 Puntschatters

### Definitie en Voorbeelden

- **Schatter**: Een statistiek $T(X_1, \dots, X_n)$ die gebruikt wordt om een parameter $\theta$ te benaderen.
- **Schatting**: De concrete waarde $T(x_1, \dots, x_n)$ voor een specifieke steekproef.
- **Voorbeelden**:
  - Populatiegemiddelde $\mu$: Steekproefgemiddelde $\overline{X}_n$.
  - Populatieproportie $p$: Steekproefproportie $\hat{P} = \frac{1}{n} \sum_{i=1}^n X_i$.

### Eigenschappen van Schatters

1. **Zuiverheid (Onvertekendheid)**:
   $E[T] = \theta$ (geen systematische afwijking).
2. **Mean Squared Error (MSE)**:
   $$
   \text{MSE}(T) = (\text{Bias}(T))^2 + \text{Var}(T).
   $$
   - Voor zuivere schatters: $\text{MSE}(T) = \text{Var}(T)$.
3. **Efficiëntie**: Schatter met kleinste variantie onder zuivere schatters.

### Schatten van Parameters in Normale Populaties

- **Populatiegemiddelde $\mu$**:
  - Schatter: $\overline{X}_n$.
  - Eigenschappen: Zuiver, $\text{Var}(\overline{X}_n) = \frac{\sigma^2}{n}$, en minimaal MSE onder normaliteit.
- **Populatievariantie $\sigma^2$**:
  - Schatter: $S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X}_n)^2$.
  - Eigenschappen: Zuiver, $E[S^2] = \sigma^2$.
  - Verdeling: $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2_{n-1}$.

### Schatten van Proporties of Kansen

- **Populatieproportie $p$**:
  - Schatter: $\hat{P} = \frac{1}{n} \sum_{i=1}^n X_i$ (relatieve frequentie).
  - Eigenschappen:
    - $E[\hat{P}] = p$.
    - $\text{Var}(\hat{P}) = \frac{p(1-p)}{n}$.
  - Voor grote $n$: $\hat{P} \approx N\left(p, \frac{p(1-p)}{n}\right)$ (via CLT).

---

## Key Points to Remember

- **Steekproefgemiddelde**:
  - Zuivere schatter voor $\mu$, variantie $\frac{\sigma^2}{n}$.
  - Betrouwbaarheid neemt toe met $n$.
- **Centrale Limietstelling**:
  - Rechtvaardigt normale benadering voor $\overline{X}_n$ bij grote steekproeven.
- **Schatters vs. Schattingen**:
  - Schatter = stochastische veranderlijke; schatting = concrete waarde.
- **Zuiverheid en MSE**:
  - Zuivere schatters hebben
