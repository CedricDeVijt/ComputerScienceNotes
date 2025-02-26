## 6.1 Vergelijken van varianties (F-test)

### Hypothesen

- **Tweezijdig**:
  $H_0: \sigma_1^2 = \sigma_2^2$ vs. $H_1: \sigma_1^2 \neq \sigma_2^2$
- **Eenzijdig**:
  $H_0: \sigma_1 \leq \sigma_2$ vs. $H_1: \sigma_1 > \sigma_2$ (of omgekeerd).

### Teststatistiek

$$
F = \frac{S_1^2}{S_2^2} \sim F_{n_1-1, n_2-1} \quad \text{onder } H_0
$$

- $S_1^2, S_2^2$: steekproefvarianties.
- **Betrouwbaarheidsinterval voor $\sigma_1^2 / \sigma_2^2$**:
  $$
  \left[ \frac{S_1^2}{S_2^2} \cdot \frac{1}{F_{n_1-1,n_2-1,1-\alpha/2}}, \frac{S_1^2}{S_2^2} \cdot F_{n_2-1,n_1-1,1-\alpha/2} \right]
  $$

### Beslissingsregel

- **Tweezijdig**: Verwerp $H_0$ als $F \notin [F_{\alpha/2}, F_{1-\alpha/2}]$.
- **Eenzijdig**: Gebruik aangepaste kritieke waarden (bijv. $F \geq F_{1-\alpha}$).

### Voorbeeld

- $s_1 = 4\mu V$ ($n_1 = 16$), $s_2 = 3\mu V$ ($n_2 = 21$), $\alpha = 5\%$.
- $f = 1.777$, kritieke waarden: $[0.362, 2.57]$.
  Conclusie: $H_0$ niet verwerpen.

## 6.2 Vergelijken van gemiddelden

### Ongepaarde waarnemingen (t-test)

#### Voorwaarden

- Normaal verdeelde steekproeven.
- Gelijkheid van varianties ($\sigma_1 = \sigma_2$), eerst testen via F-test.

#### Gepoolde variantie

$$
\tilde{S}^2 = \frac{(n_1-1)S_1^2 + (n_2-1)S_2^2}{n_1 + n_2 - 2}
$$

#### Teststatistiek

$$
T = \frac{\overline{X} - \overline{Y}}{\tilde{S} \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim t_{n_1 + n_2 - 2} \quad \text{onder } H_0
$$

#### Betrouwbaarheidsinterval voor $\mu_1 - \mu_2$

$$
\left[ \overline{x} - \overline{y} \pm t_{n_1+n_2-2,1-\alpha/2} \cdot \tilde{s} \sqrt{\frac{1}{n_1} + \frac{1}{n_2}} \right]
$$

#### Voorbeeld

- Kunstmesttest: $\overline{x} = 5.8$, $\overline{y} = 4.9$, $\tilde{s} = 0.379$, $t = 4.59$.
  Conclusie: Verwerp $H_0$ ($p = 0.0003$).

### Gepaarde waarnemingen (paired t-test)

#### Stappen

1. Bereken verschillen $D_i = X_i - Y_i$.
2. Test $H_0: \mu_D = 0$.

#### Teststatistiek

$$
T = \frac{\overline{D}}{S_D / \sqrt{n}} \sim t_{n-1} \quad \text{onder } H_0
$$

#### Voorbeeld

- Benzinevergelijking: $\overline{D} = -2.8$, $s_D = 3.853$, $t = -2.298$.
  Conclusie: Significant bij $\alpha = 5\%$, niet bij $\alpha = 1\%$.

## 6.3 Vergelijken van twee proporties

### Hypothesen

- $H_0: p_1 = p_2$ vs. $H_1: p_1 \neq p_2$.

### Teststatistiek (grote steekproeven)

$$
Z = \frac{\widehat{p}_1 - \widehat{p}_2}{\sqrt{\widehat{p}_0(1-\widehat{p}_0)\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}} \approx \mathcal{N}(0,1)
$$

met $\widehat{p}_0 = \frac{n_1\widehat{p}_1 + n_2\widehat{p}_2}{n_1 + n_2}$.

### Betrouwbaarheidsinterval

$$
\left[ (\widehat{p}_1 - \widehat{p}_2) \pm z_{1-\alpha/2} \sqrt{\frac{\widehat{p}_1(1-\widehat{p}_1)}{n_1} + \frac{\widehat{p}_2(1-\widehat{p}_2)}{n_2}} \right]
$$

---

## Key Points to Remember

- **F-test**: Gebruik voor variantievergelijking; let op tweezijdige vs. eenzijdige kritieke waarden.
- **t-test voor ongepaarde data**: Vereist gelijke varianties (eerst F-test uitvoeren).
- **Gepoolde variantie**: Combineert steekproefvarianties bij gelijke $\sigma$.
- **Gepaarde t-test**: Gebruik verschillen $D_i$ om afhankelijkheid te behandelen.
- **Proportietest**: Gebruik gemengde proportie $\widehat{p}_0$ onder $H_0$.
- **Significantieniveau**: Pas kritieke waarden en $p$-waarden aan voor eenzijdige vs. tweezijdige tests.
- **Voorbeelden**: Illustreren hoe teststatistieken en beslissingen worden berekend.
