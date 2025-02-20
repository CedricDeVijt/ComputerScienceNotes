## 3.1 Definitie en Eigenschappen van het Steekproefgemiddelde

- **Steekproefgemiddelde**: Een schatter voor het populatiegemiddelde, gedefinieerd als:
  $$
  \overline{X}_n = \frac{1}{n} \sum_{i=1}^n X_i
  $$
  waarbij $X_1, \ldots, X_n$ onafhankelijke en identiek verdeelde (i.i.d.) stochastische variabelen zijn.
- **Verwachting**:
  $$
  \mathrm{E}[\overline{X}_n] = \mathrm{E}[X_1] = \mu
  $$
- **Variantie**:
  $$
  \mathrm{Var}[\overline{X}_n] = \frac{\sigma^2}{n}
  $$

## 3.2 Verdeling van het Steekproefgemiddelde

- Voor **normaal verdeelde populaties** ($X_i \sim \mathcal{N}(\mu, \sigma^2)$):
  $$
  \overline{X}\_n \sim \mathcal{N}\left(\mu, \frac{\sigma^2}{n}\right)
  $$
- Voor niet-normale populaties benadert de verdeling van $\overline{X}\_n$ een normale verdeling voor grote $n$ (zie CLT).

## 3.3 Centrale Limietstelling (CLT)

- **Voorwaarden**:
  - $X_1, X_2, \ldots$ zijn i.i.d. met $\mathrm{E}[X_i] = \mu$ en $\mathrm{Var}[X_i] = \sigma^2 < \infty$.
- **Resultaat**:
  $$
  \frac{\sqrt{n}(\overline{X}\_n - \mu)}{\sigma} \xrightarrow{D} \mathcal{N}(0,1) \quad \text{als } n \rightarrow \infty
  $$
- **Implicatie**:
  $$
  \overline{X}\_n \approx \mathcal{N}\left(\mu, \frac{\sigma^2}{n}\right) \quad \text{voor grote } n
  $$

# 3 Puntschatters en hun Eigenschappen

## 3.4 Definitie van Schatters en Statistieken

- **Statistiek**: Een functie van de steekproef ($T(X_1, \ldots, X_n)$) die geen afhankelijkheid heeft van onbekende parameters.
- **Schatter**: Een statistiek gebruikt om een parameter $\theta$ te schatten.
- **Schatting**: De concrete waarde van een schatter voor een gegeven steekproef.

## 3.5 Eigenschappen van Schatters

1. **Zuiverheid (Onvertekendheid)**:
   $$
   \mathrm{E}[T] = \theta \quad \forall \theta
   $$
   - Voorbeeld: $\overline{X}\_n$ is zuiver voor $\mu$.
2. **Mean Squared Error (MSE)**:
   $$
   \mathrm{MSE}(T) = (\text{bias}(T))^2 + \mathrm{Var}(T)
   $$
   - Voor zuivere schatters: $\mathrm{MSE}(T) = \mathrm{Var}(T)$.

## 3.6 Schatten van Parameters in Normale Verdeling

- **Populatiegemiddelde $\mu$**:
  - Zuivere schatter: $\overline{X}\_n$.
  - MSE: $\frac{\sigma^2}{n}$.
  - Optimale schatter onder normaliteit (kleinste variantie).
- **Populatievariantie $\sigma^2$**:
  - Zuivere schatter:
    $$
    S^2 = \frac{1}{n-1} \sum\_{i=1}^n (X_i - \overline{X}\_n)^2
    $$
  - Verdeling: $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2\_{n-1}$ (Helmert's stelling).

## 3.7 Schatten van Proporties (Bernoulli Verdeling)

- **Proportie $p$**:
  $$
  \widehat{P} = \overline{X}_n = \frac{1}{n} \sum_{i=1}^n X_i \quad (X_i \sim \text{Bernoulli}(p))
  $$
- **Eigenschappen**:
  $$
  \mathrm{E}[\widehat{P}] = p, \quad \mathrm{Var}[\widehat{P}] = \frac{p(1-p)}{n}
  $$
- Voor grote $n$: $\widehat{P} \approx \mathcal{N}\left(p, \frac{p(1-p)}{n}\right)$.

## Key Points to Remember

- Het **steekproefgemiddelde** $\overline{X}\_n$ is een zuivere schatter voor $\mu$ met variantie $\sigma^2/n$.
- De **Centrale Limietstelling** stelt dat $\overline{X}\_n$ normaal verdeeld is voor grote $n$, ongeacht de oorspronkelijke verdeling.
- **Zuivere schatters** hebben een bias van 0; de variantie bepaalt hun nauwkeurigheid.
- **MSE** combineert bias en variantie: $\mathrm{MSE} = \text{bias}^2 + \mathrm{Var}$.
- Voor $\sigma^2$ gebruik je $S^2 = \frac{1}{n-1} \sum (X_i - \overline{X}\_n)^2$ om zuiverheid te garanderen.
- Proporties worden geschat met $\widehat{P}$, dat normaal benaderd wordt voor grote steekproeven.
