## 1.1 Discrete Univariate Verdelingen

### Discrete Uniforme Verdeling

- **Definitie**: Een stochastische variabele $X$ is uniform verdeeld op een eindig universum $\Omega = \{1, 2, ..., n\}$ als elke uitkomst even waarschijnlijk is.
- **Kansen**: $P(X = j) = \frac{1}{n}$ voor $j = 1, ..., n$.
- **Kentallen**:
  - $\mathrm{E}[X] = \frac{n+1}{2}$
  - $\mathrm{Var}[X] = \frac{(n^2 - 1)}{12}$

### Bernoulli Verdeling

- **Definitie**: Modelleert experimenten met twee uitkomsten (succes: 1, mislukking: 0). Notatie: $X \sim B(1, p)$.
- **Kansen**:
  - $P(X = 1) = p$
  - $P(X = 0) = 1 - p$
- **Kentallen**:
  - $\mathrm{E}[X] = p$
  - $\mathrm{Var}[X] = p(1 - p)$

### Binomiale Verdeling

- **Definitie**: Telt het aantal successen in $n$ onafhankelijke Bernoulli-experimenten. Notatie: $Y \sim B(n, p)$.
- **Kansen**: $P(Y = k) = \binom{n}{k} p^k (1-p)^{n-k}$.
- **Kentallen**:
  - $\mathrm{E}[Y] = np$
  - $\mathrm{Var}[Y] = np(1 - p)$
- **Eigenschap**: Als $Y_1 \sim B(n_1, p)$ en $Y_2 \sim B(n_2, p)$ onafhankelijk zijn, dan $Y_1 + Y_2 \sim B(n_1 + n_2, p)$.

### Negatief-Binomiale Verdeling

- **Definitie**: Telt het aantal mislukkingen voor het $r$-de succes. Notatie: $X \sim NB(r, \theta)$.
- **Kansen**: $P(X = j) = \binom{j + r - 1}{j} (1 - \theta)^r \theta^j$.
- **Toepassing**: Modelleert wachttijden tot een bepaald aantal successen.

### Poissonverdeling

- **Definitie**: Modelleert zeldame gebeurtenissen in een vast interval. Notatie: $X \sim \mathcal{P}(\alpha)$.
- **Kansen**: $P(X = j) = \frac{\alpha^j}{j!} e^{-\alpha}$.
- **Kentallen**:
  - $\mathrm{E}[X] = \alpha$
  - $\mathrm{Var}[X] = \alpha$
- **Eigenschap**: Als $X_1 \sim \mathcal{P}(\alpha_1)$ en $X_2 \sim \mathcal{P}(\alpha_2)$ onafhankelijk zijn, dan $X_1 + X_2 \sim \mathcal{P}(\alpha_1 + \alpha_2)$.

## 1.2 Continue Univariate Verdelingen

### Continue Uniforme Verdeling

- **Definitie**: Gelijkmatige verdeling over interval $[a, b]$. Notatie: $X \sim U[a, b]$.
- **Dichtheid**: $f*{a,b}(x) = \frac{1}{b - a} \cdot 1*{[a,b]}(x)$.
- **Kentallen**:
  - $\mathrm{E}[X] = \frac{a + b}{2}$
  - $\mathrm{Var}[X] = \frac{(b - a)^2}{12}$

### Normale Verdeling (Gaussiaans)

- **Standaardnormaal**: $Z \sim \mathcal{N}(0, 1)$ met dichtheid $\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2/2}$.
- **Algemene Normaalverdeling**: $X \sim \mathcal{N}(\mu, \sigma^2)$ via $X = \sigma Z + \mu$.
  - Dichtheid: $f\_{\mu,\sigma}(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$.
  - $\mathrm{E}[X] = \mu$, $\mathrm{Var}[X] = \sigma^2$.
- **Eigenschap**: Lineaire combinaties van normale verdelingen zijn ook normaal.

### Chi-Kwadraat Verdeling ($\chi^2_n$)

- **Definitie**: Som van kwadraten van $n$ onafhankelijke standaardnormale variabelen. Notatie: $X \sim \chi^2_n$.
- **Kentallen**:
  - $\mathrm{E}[X] = n$
  - $\mathrm{Var}[X] = 2n$
- **Eigenschap**: Als $X*1 \sim \chi^2*{n*1}$ en $X_2 \sim \chi^2*{n*2}$ onafhankelijk, dan $X_1 + X_2 \sim \chi^2*{n_1 + n_2}$.

### Student t-Verdeling ($t_n$)

- **Definitie**: $T = \frac{Z}{\sqrt{X/n}}$ met $Z \sim \mathcal{N}(0,1)$ en $X \sim \chi^2_n$. Notatie: $T \sim t_n$.
- **Eigenschappen**:
  - Symmetrisch rond 0.
  - $\mathrm{Var}[T] = \frac{n}{n - 2}$ (voor $n > 2$).

### F-Verdeling

- **Definitie**: Verhouding van twee chi-kwadraat verdeelde variabelen. Notatie: $X \sim F\_{m,n}$.
- **Eigenschap**: $F*{m,n}(x) = 1 - F*{n,m}(\frac{1}{x})$.

## 1.3 Belangrijkste Punten om te Onthouden

- **Discrete Verdelingen**:
  - Uniform: Gelijkmatige kansen over eindige uitkomsten.
  - Bernoulli: Modelleert binaire uitkomsten.
  - Binomiaal: Telt successen in onafhankelijke herhalingen.
  - Poisson: Telt gebeurtenissen in vaste intervallen met vaste snelheid.
- **Continue Verdelingen**:
  - Normaal: Symmetrische klokvorm, centraal in statistische inferentie.
  - Chi-kwadraat: Gebruikt in hypothesetesten (bv. variantie-analyse).
  - t-verdeling: Voor kleine steekproeven; benadert normaal bij grote $n$.
  - F-verdeling: Vergelijkt varianties tussen groepen.
- **Formules**:
  - $\mathrm{E}[X]$ en $\mathrm{Var}[X]$ voor elke verdeling.
  - Additiviteitseigenschappen (bv. Poisson, Binomiaal, $\chi^2$).
- **Toepassingen**:
  - Bernoulli/Binomiaal: Succes/mislukking-modellen.
  - Poisson: Zeldame gebeurtenissen (bv. callcenter-data).
  - Normaal: Natuurlijke fenomenen (bv. IQ-scores, meetfouten).
