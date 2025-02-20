## 4.1 **Hoofdstuk 1: Betrouwbaarheidsintervallen**

### **1.1 Inleiding**

Een betrouwbaarheidsinterval (BI) is een methode om een schatting te geven voor een onbekende parameter met een bepaalde zekerheid.

#### **Definitie**

Een interval [L(X₁, ..., Xₙ), R(X₁, ..., Xₙ)] is een (1 - α) BI indien:

$$P(\theta \in [L(X_1, ..., X_n), R(X_1, ..., X_n)]) = 1 - \alpha$$

waarbij:

- $1 - \alpha$ het **betrouwbaarheidsniveau** is (bijvoorbeeld 90%, 95%, 99%)
- $\alpha$ het **significantieniveau** is

Een BI is niet uniek en kan **tweezijdig** of **eenzijdig** zijn:

- **Tweezijdig:** $P(\theta < L(X_1, ..., X_n)) = P(\theta > R(X_1, ..., X_n)) = \alpha/2$
- **Linkseenzijdig:** $[-\infty, R(X_1, ..., X_n)]$
- **Rechtseenzijdig:** $[L(X_1, ..., X_n), \infty]$

### **1.2 Algemene strategie voor BI-constructie**

1. Kies een geschikte schatter T voor $\theta$.
2. Bepaal de verdeling van een functie $h(T, \theta)$, onafhankelijk van $\theta$.
3. Zoek geschikte kwartielen $a$ en $b$ zodat:
   $$P(a \leq h(T, \theta) \leq b) = 1 - \alpha$$
4. Herformuleer de ongelijkheid zodat $\theta$ in het midden staat.

## 4.2 **Hoofdstuk 2: Betrouwbaarheidsintervallen voor specifieke parameters**

### **2.1 Gemiddelde van een normale verdeling met bekende variantie**

We nemen een steekproef van grootte $n$ uit een normale verdeling $N(\mu, \sigma^2)$ waarbij $\sigma$ bekend is.

#### **Betrouwbaarheidsinterval**

Uit de standaardisering van de steekproefgemiddelde volgt:
$$Z = \frac{X_n - \mu}{\sigma / \sqrt{n}} \sim N(0,1)$$

Voor een 95% BI geldt:
$$P(-1.96 \leq Z \leq 1.96) = 95%$$
$$P(X_n - 1.96 \frac{\sigma}{\sqrt{n}} \leq \mu \leq X_n + 1.96 \frac{\sigma}{\sqrt{n}}) = 95%$$

#### **Voorbeeld**

Bij een bergmeting met $\sigma = 2m$, $n = 16$, en $X_n = 3118.5m$, is het 95% BI:
$$[3117.52m, 3119.48m]$$

### **2.2 Variantie van een normale verdeling**

We willen een BI voor $\sigma^2$ wanneer zowel $\mu$ als $\sigma$ onbekend zijn.

#### **Betrouwbaarheidsinterval**

We gebruiken de steekproefvariantie:
$$S^2 = \frac{1}{n-1} \sum (X*i - X_n)^2$$
Uit de verdeling $\chi^2$ volgt:
$$P\left( \frac{(n-1)S^2}{\chi^2*{n-1,1-\alpha/2}} \leq \sigma^2 \leq \frac{(n-1)S^2}{\chi^2\_{n-1,\alpha/2}} \right) = 1 - \alpha$$

#### **Voorbeeld**

Bij 16 metingen met steekproefvariantie $S^2 = 5.76cm^2$, is het 95% BI:
$$[1.77cm, 3.72cm]$$

### **2.3 Gemiddelde van een normale verdeling (onbekende variantie)**

Wanneer $\sigma$ onbekend is, gebruiken we de Student t-verdeling.

#### **Betrouwbaarheidsinterval**

Uit:
$$T = \frac{X*n - \mu}{S / \sqrt{n}} \sim t*{n-1}$$
volgt:
$$P(X*n - t*{n-1,1-\alpha/2} \frac{S}{\sqrt{n}} \leq \mu \leq X*n + t*{n-1,1-\alpha/2} \frac{S}{\sqrt{n}}) = 1 - \alpha$$

#### **Voorbeeld**

Bij een steekproef van 12 metingen van paasei-gewichten met $X_n = 177.66g$ en $S = 4.774g$, is het 95% BI:
$$[174.6g, 180.7g]$$

### **2.4 Proportie**

Voor een binaire variabele (succes/mislukking) met proportie $p$ geldt:
$$\hat{P} = \frac{X}{n}$$
Bij grote steekproeven ($n > 30$, $np > 5$, $nq > 5$) kunnen we de normale benadering gebruiken:
$$\hat{P} \sim N(p, \frac{pq}{n})$$

#### **Betrouwbaarheidsinterval**

$$P(\hat{P} - z*{1-\alpha/2} \sqrt{\frac{\hat{P}(1-\hat{P})}{n}} \leq p \leq \hat{P} + z*{1-\alpha/2} \sqrt{\frac{\hat{P}(1-\hat{P})}{n}}) = 1 - \alpha$$

#### **Voorbeeld**

Bij een verkiezingsenquête met $\hat{P} = 55\%$, $n = 200$:

- **95% BI**: $[48.1\%, 61.9\%]$
- **99% BI**: $[45.9\%, 64.1\%]$

## 4.3 **Hoofdstuk 3: Belangrijke punten om te onthouden**

- **Betrouwbaarheidsintervallen** geven een schatting van een onbekende parameter met een kans van $1 - \alpha$.
- **Voor een normaal gemiddelde met bekende variantie** gebruiken we de standaardnormale verdeling.
- **Voor een normaal gemiddelde met onbekende variantie** gebruiken we de Student t-verdeling.
- **Voor variantie van een normale verdeling** gebruiken we de $\chi^2$-verdeling.
- **Voor proporties** kunnen we een normale benadering gebruiken bij grote steekproeven.
- **BI’s worden smaller bij grotere steekproeven** en breder bij hogere betrouwbaarheid.
