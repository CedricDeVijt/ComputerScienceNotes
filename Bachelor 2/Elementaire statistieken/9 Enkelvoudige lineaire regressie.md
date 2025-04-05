## 9.1 Lineair Model

### Modelformulering

- Gegevens: $\{(x_1, y_1), \ldots, (x_n, y_n)\}$.
- **Model**:
  $$Y_i = \alpha + \beta x_i + \varepsilon_i$$
  waarbij $\varepsilon_i \sim N(0, \sigma_\varepsilon^2)$ (onafhankelijke normaal verdeelde fouten).
- **Veronderstellingen**:
  - Homoscedasticiteit: variantie van $\varepsilon_i$ is constant.
  - $x_i$ worden zonder meetfout verkregen.
  - Lineaire relatie tussen $Y_i$ en $x_i$.

### Betekenis van Parameters

- **Intercept ($\alpha$)**: Gemiddelde waarde van $Y$ bij $x = 0$.
- **Hellingscoëfficiënt ($\beta$)**: Verandering in gemiddelde $Y$ per eenheidstoename in $x$.
  $$E(Y|x+1) - E(Y|x) = \beta$$

## 9.2 Parameterschatting

### Methode van Kleinste Kwadraten

- **Residu**: $e_i = y_i - \hat{y}_i = y_i - (a + b x_i)$.
- Doel: Minimaliseer $\sum_{i=1}^n e_i^2$.
- **Normaalvergelijkingen**:
  $$
  \begin{cases}
  \sum x_i y_i = a \sum x_i + b \sum x_i^2 \\
  \sum y_i = n a + b \sum x_i
  \end{cases}
  $$
- **Schatters**:
  $$
  \hat{\beta} = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sum (x_i - \bar{x})^2}, \quad
  \hat{\alpha} = \bar{y} - \hat{\beta} \bar{x}
  $$
- **Schatter voor $\sigma_\varepsilon^2$**:
  $$s_\varepsilon^2 = \frac{\sum e_i^2}{n-2}$$

## 9.3 Betrouwbaarheidsintervallen en Hypothesetesten

### Variantie van Fouten ($\sigma_\varepsilon^2$)

- **Betrouwbaarheidsinterval**:
  $$
  \left[ \frac{(n-2)s_\varepsilon^2}{\chi_{n-2,1-\alpha/2}^2}, \frac{(n-2)s_\varepsilon^2}{\chi_{n-2,\alpha/2}^2} \right]
  $$
- **Hypothesetest voor $\sigma_\varepsilon^2$**:
  Gebruik $\frac{(n-2)s_\varepsilon^2}{\sigma_0^2} \sim \chi_{n-2}^2$.

### Testen voor $\alpha$ en $\beta$

- **Teststatistiek voor $\beta = 0$**:
  $$
  t = \frac{\hat{\beta}}{s_\varepsilon} \sqrt{\sum (x_i - \bar{x})^2} \sim t_{n-2}
  $$
- **Teststatistiek voor $\alpha = 0$**:
  $$
  t = \frac{\hat{\alpha} \sqrt{\sum (x_i - \bar{x})^2}}{s_\varepsilon \sqrt{\bar{x}^2 + \frac{1}{n} \sum (x_i - \bar{x})^2}} \sim t_{n-2}
  $$

## 9.4 Toepassing: Voorbeeldanalyse

### Dataset: Maandelijkse Verliezen

- **Gegevens**: Verlies ($y$) vs. maand ($x$) voor 5 maanden.
- **Resultaten**:
  - $\hat{\beta} = -3$, $\hat{\alpha} = 13$, $s_\varepsilon^2 = 4/3$.
  - Voorspelling voor $x=6$: $\hat{y} = -5$ (extrapolatie!).
- **Hypothesetesten**:
  - Hellingscoëfficiënt $\beta$ en intercept $\alpha$ zijn significant verschillend van 0 ($p < 0.05$).

### Case Study: Huisprijzen en Belastingen

- **Regressieresultaten (R-output)**:
  - Hellingscoëfficiënt significant ($p < 0.001$), intercept niet.
  - **Residuenanalyse**: Heteroscedasticiteit en afwijking van normaliteit.
- **Log-transformatie**:
  - Verbeterde homoscedasticiteit, maar resterende afwijkingen in QQ-plot.

## 9.5 Diagnostiek en Modelvalidatie

### Residuenanalyse

- **Homoscedasticiteit**: Gelijkmatige spreiding van residuen rond nul.
- **QQ-plot**: Controleer normaliteit van residuen.
- **Invloedrijke punten**: Extreme waarden kunnen de regressielijn beïnvloeden.

### Data-transformaties

- **Log-transformatie**: Gebruikt om niet-lineaire relaties en heteroscedasticiteit te verminderen.

---

## Key Points to Remember

- **Modelvergelijking**: $Y_i = \alpha + \beta x_i + \varepsilon_i$ met $\varepsilon_i \sim N(0, \sigma_\varepsilon^2)$.
- **Schatters**:
  - $\hat{\beta} = \frac{s_{XY}}{s_X^2}$, $\hat{\alpha} = \bar{y} - \hat{\beta}\bar{x}$.
  - $s_\varepsilon^2 = \frac{\sum e_i^2}{n-2}$.
- **Hypothesetesten**:
  - Gebruik $t$-verdeling voor $\alpha$ en $\beta$, $\chi^2$-verdeling voor $\sigma_\varepsilon^2$.
- **Residuenanalyse**: Controleer homoscedasticiteit en normaliteit.
- **Extrapolatie**: Voorspellingen buiten het $x$-bereik zijn onbetrouwbaar.
- **Transformaties**: Log-transformatie kan heteroscedasticiteit verminderen.
