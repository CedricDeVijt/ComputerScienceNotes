## 5.1 **Hoofdstuk 1: Inleiding tot Hypothesetesten**

### **1.1 Wat is een Hypothesetest?**

- Beslissingsprobleem: kiezen tussen twee tegengestelde hypothesen.
- Nulhypothese (**H0**) versus alternatieve hypothese (**H1**).
- Doel: **H0 verwerpen ten gunste van H1**, indien er voldoende bewijs is.

### **1.2 De vier stappen van een hypothesetest**

1. **Hypothesen opstellen**: H0 en H1 formuleren.
2. **Teststatistiek definiëren**: een grootheid berekenen uit de steekproef.
3. **Beslissingsregel bepalen**: significantieniveau (α) en criterium vaststellen.
4. **Fouten identificeren**:
   - Type I fout (α): H0 onterecht verwerpen.
   - Type II fout (β): H0 onterecht behouden.

## 5.2 **Hoofdstuk 2: Hypothesetesten voor het gemiddelde**

### **2.1 Gemiddelde van een normale verdeling met bekende variantie**

#### **2.1.1 Tweezijdige z-test**

- Hypothesen:
  - H0: μ = μ0
  - H1: μ ≠ μ0
- Teststatistiek:
  $$Z = \frac{X - \mu_0}{\sigma / \sqrt{n}} \sim N(0,1)$$
- Beslissingsregel:
  - H0 verwerpen als $|Z| > z\_{1-α/2}$

#### **2.1.2 Eenzijdige z-test**

- Hypothesen:
  - Rechsteenzijdig: H0: μ ≤ μ0, H1: μ > μ0
  - Linkseenzijdig: H0: μ ≥ μ0, H1: μ < μ0
- Beslissingsregel:
  - H0 verwerpen als $Z > z*{1-α}$ of $Z < -z*{1-α}$.

### **2.2 Gemiddelde van een normale verdeling met onbekende variantie**

#### **2.2.1 Tweezijdige t-test**

- Teststatistiek:
  $$T = \frac{X - \mu*0}{S / \sqrt{n}} \sim t*{n-1}$$
- H0 verwerpen als $|T| > t\_{n-1,1-α/2}$.

#### **2.2.2 Eenzijdige t-test**

- H0 verwerpen als $T > t*{n-1,1-α}$ of $T < -t*{n-1,1-α}$.

### **2.3 P-waarde**

- Kans om een waarde minstens zo extreem als de geobserveerde testwaarde te verkrijgen.
- H0 verwerpen als $p < α$.

## 5.3 **Hoofdstuk 3: Hypothesetesten voor variantie**

- **Chi-kwadraat test** om varianties te vergelijken.
- Teststatistiek:
  $$X^2 = \frac{(n-1)S^2}{σ*0^2} \sim χ^2*{n-1}$$

## 5.4 **Hoofdstuk 4: Hypothesetesten voor proporties**

### **4.1 Benaderende test (grote steekproef)**

- Teststatistiek:
  $$Z = \frac{̂p - p_0}{\sqrt{p_0(1-p_0)/n}} \sim N(0,1)$$
- H0 verwerpen als $|Z| > z\_{1-α/2}$.

### **4.2 Exacte test (kleine steekproef)**

- Gebaseerd op de binomiaalverdeling.
- Directe kansberekening onder H0.

## 5.5 **Hoofdstuk 5: Normaliteitsassumptie**

- QQ-plot gebruiken om normaliteit te beoordelen.
- Tests zoals Shapiro-Wilk test.
- Indien niet normaal: transformaties of niet-parametrische testen overwegen.

## 5.6 **Belangrijke punten om te onthouden**

- Hypothesetesten helpen bij besluitvorming onder onzekerheid.
- Een **type I fout** betekent dat een correcte nulhypothese wordt verworpen.
- Een **type II fout** betekent dat een foutieve nulhypothese niet wordt verworpen.
- **P-waarde**: hoe kleiner, hoe sterker het bewijs tegen H0.
- **Z-test** wordt gebruikt als de variantie bekend is, **t-test** als de variantie onbekend is.
- **Bij kleine steekproeven** is een exacte test nodig voor proporties.
- **Normaliteitsveronderstelling** is belangrijk, vooral bij kleine steekproeven.
