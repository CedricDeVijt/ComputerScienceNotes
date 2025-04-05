## 4.1 Inleiding tot Betrouwbaarheidsintervallen

- **Doel**: Nauwkeurigheid van puntschatters evalueren door een interval te construeren waarin de parameter met bepaalde zekerheid ligt.
- **Definitie**: Een interval $[L, R]$ is een $(1-\alpha)$-betrouwbaarheidsinterval (BI) als
  $P(\theta \in [L, R]) = 1 - \alpha$.
  Hierbij is $1 - \alpha$ het betrouwbaarheidsniveau (b.v. 0.95) en $\alpha$ het significantieniveau.

### Typen Betrouwbaarheidsintervallen

1. **Tweezijdig BI**:
   $P(\theta < L) = P(\theta > R) = \alpha/2$.
2. **Eenzijdig BI**:
   - Links: $[-\infty, R]$
   - Rechts: $[L, \infty]$.

## 4.2 Constructiestrategie voor Betrouwbaarheidsintervallen

1. **Kies een schatter $T$** voor $\theta$.
2. **Bepaal de verdeling** van een functie $h(T, \theta)$ die onafhankelijk is van $\theta$.
3. **Vind kwartielen $a$ en $b$** zodat $P(a \leq h(T, \theta) \leq b) = 1 - \alpha$.
4. **Herrangschik de ongelijkheid** om $\theta$ in het midden te isoleren.

## 4.3 Gemiddelde van Normale Verdeling met Bekende Variantie

### Aannames

- Steekproef: $X_1, \dots, X_n \sim N(\mu, \sigma^2)$ met $\sigma^2$ bekend.
- Schatter: Steekproefgemiddelde $\bar{X}_n \sim N\left(\mu, \frac{\sigma^2}{n}\right)$.

### Betrouwbaarheidsinterval

$$
\left[ \bar{x}_n - z_{1-\alpha/2} \frac{\sigma}{\sqrt{n}},\ \bar{x}_n + z_{1-\alpha/2} \frac{\sigma}{\sqrt{n}} \right]
$$

- **Interpretatie**: In 95% van de herhaalde steekproeven bevat het interval $\mu$.

### Voorbeeld

- $\sigma = 2$, $n = 16$, $\bar{x}_n = 3118.5$:
  95% BI = $[3118.5 \pm 1.96 \cdot \frac{2}{\sqrt{16}}] = [3117.52, 3119.48]$.

## 4.4 Variantie van Normale Verdeling

### Aannames

- Steekproef: $X_1, \dots, X_n \sim N(\mu, \sigma^2)$ met $\mu$ en $\sigma^2$ onbekend.
- Schatter: Steekproefvariantie $S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)^2$.

### Verdeling en Betrouwbaarheidsinterval

- $(n-1)\frac{S^2}{\sigma^2} \sim \chi^2_{n-1}$.
- BI voor $\sigma^2$:
  $$
  \left[ \frac{(n-1)s^2}{\chi^2_{n-1, 1-\alpha/2}},\ \frac{(n-1)s^2}{\chi^2_{n-1, \alpha/2}} \right]
  $$
- BI voor $\sigma$: Neem vierkantswortel van bovenstaande.

### Voorbeeld

- $n = 16$, $s^2 = 5.76$:
  95% BI voor $\sigma = \left[\sqrt{\frac{15 \cdot 5.76}{27.488}},\ \sqrt{\frac{15 \cdot 5.76}{6.262}}\right] = [1.77, 3.72]$.

## 4.5 Gemiddelde van Normale Verdeling met Onbekende Variantie

### Aannames

- $\sigma^2$ wordt geschat via $S^2$.
- Schatter: $T = \frac{\bar{X}_n - \mu}{S/\sqrt{n}} \sim t_{n-1}$.

### Betrouwbaarheidsinterval

$$
\left[ \bar{x}_n - t_{n-1, 1-\alpha/2} \frac{s}{\sqrt{n}},\ \bar{x}_n + t_{n-1, 1-\alpha/2} \frac{s}{\sqrt{n}} \right]
$$

### Voorbeeld

- Paasei-gewichten: $n = 12$, $\bar{x} = 177.66$, $s = 4.774$:
  95% BI = $[177.66 \pm 2.201 \cdot \frac{4.774}{\sqrt{12}}] = [174.6, 180.7]$.

## 4.6 Betrouwbaarheidsinterval voor Proportie

### Aannames

- Steekproefgrootte $n \geq 30$, $np \geq 5$, $n(1-p) \geq 5$.
- Schatter: $\hat{p} = \frac{\text{aantal successen}}{n} \approx N\left(p, \frac{p(1-p)}{n}\right)$.

### Betrouwbaarheidsinterval

$$
\left[ \hat{p} - z_{1-\alpha/2} \sqrt{\frac{\hat{p}(1-\hat{p})}{n}},\ \hat{p} + z_{1-\alpha/2} \sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \right]
$$

### Voorbeeld

- Enquête: $n = 200$, $\hat{p} = 0.55$:
  95% BI = $[0.55 \pm 1.96 \cdot 0.0352] = [0.481, 0.619]$.

---

## Key Points to Remember

- **Betrouwbaarheidsniveau**: $1 - \alpha$ geeft de kans dat het interval de parameter bevat bij herhaalde steekproeven.
- **Z-score vs. t-score**:
  - Gebruik $z$ bij bekende $\sigma$, $t$ bij onbekende $\sigma$ (met $n-1$ vrijheidsgraden).
- **Chi-kwadraatverdeling**: Voor variantie-intervallen, let op asymmetrische kwantielen.
- **Proporties**: Benadering via normale verdeling vereist grote $n$ en $np \geq 5$.
- **Breedte van BI**:
  - Afneemt met $\sqrt{n}$.
  - Toeneemt bij hogere betrouwbaarheid (lagere $\alpha$).
- **Interpretatie**: Een 95% BI betekent niet dat $\mu$ met 95% kans in het interval ligt, maar dat 95% van de intervallen $\mu$ bevatten bij herhaling.
