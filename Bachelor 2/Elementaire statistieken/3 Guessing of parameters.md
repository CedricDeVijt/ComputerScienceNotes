# 3 **Elementaire Statistiek**

## 3.1 **Hoofdstuk 1: Het Schatten van Parameters**

### **1.1 Inleiding**

Statistische modellen bevatten vaak onbekende parameters zoals:

- **µ en σ²** in het normale model
- **α** in het Poisson model
- **p** in het binomiale model

Deze parameters worden geschat aan de hand van steekproeven. In dit hoofdstuk behandelen we:

1. Het verkrijgen van schattingen uit steekproeven
2. De betrouwbaarheid van deze schattingen

### **1.2 Steekproefgemiddelde als Schatter**

Het **steekproefgemiddelde (X̄n)** is een schatting van het **populatiegemiddelde (E[X])**. Omdat het afhankelijk is van de steekproef, is het een **stochastische veranderlijke (s.v.)**.

Formules:

- **Steekproefgemiddelde (X̄n):**
  $$X̄n = \frac{1}{n} \sum\_{i=1}^{n} X_i$$
- **Verwachtingswaarde:**
  $$E[X̄n] = E[X]$$
- **Variantie:**
  $$Var[X̄n] = \frac{σ²}{n}$$
  Dit betekent dat een grotere steekproef leidt tot een kleinere variantie.

### **1.3 Centrale Limietstelling (CLS)**

De CLS stelt dat als **X1, X2, ..., Xn** onafhankelijke en identiek verdeelde s.v. zijn, dan geldt:

- Voor voldoende grote n:
  $$X̄n \approx N(µ, \frac{σ²}{n})$$
- Voor de gestandaardiseerde som:
  $$\frac{X̄n - µ}{σ / \sqrt{n}} \approx N(0,1)$$
  Dit impliceert dat de verdeling van het gemiddelde voor grote steekproeven naar een normale verdeling neigt.

## 3.2 **Hoofdstuk 2: Puntschatters**

### **2.1 Wat is een Schatter?**

Een **schatter** is een functie van een steekproef die een onbekende parameter **θ** benadert. Formeel:

- **Definitie:** Een schatter T is een toevalsveranderlijke die alleen afhangt van de steekproef en niet van de onbekende parameter θ.

**Voorbeeld:**

- Steekproefgemiddelde $X̄n$ is een schatter voor $µ$
- Steekproefmediaan kan ook een schatter voor $µ$ zijn

### **2.2 Eigenschappen van een Goede Schatter**

Een goede schatter heeft de volgende eigenschappen:

- **Onvertekendheid (unbiasedness):**
  $$E[T] = θ$$
  Dit betekent dat de schatter gemiddeld genomen de juiste waarde geeft.
- **Minimale variantie:** De schatter moet zo min mogelijk spreiding hebben.
- **Mean Squared Error (MSE):**
  $$MSE(T) = Var(T) + (Bias(T))²$$
  Een schatter met lage MSE is beter.

### **2.3 Schatten van de Parameters van een Normale Verdeling**

Voor een normale populatie N(µ, σ²) worden de volgende schatters gebruikt:

- **Steekproefgemiddelde:**
  $$X̄n = \frac{1}{n} \sum\_{i=1}^{n} X_i$$
  Dit is een onvertekende schatter van **µ**.
- **Steekproefvariantie:**
  $$S² = \frac{1}{n-1} \sum\_{i=1}^{n} (X_i - X̄n)²$$
  Dit is een onvertekende schatter van **σ²**.

**Opmerking:** X̄n en S² zijn onafhankelijk volgens de **Stelling van Helmert**.

### **2.4 Schatten van Proporties**

Voor een rij onafhankelijke Bernoulli-variabelen met succes-kans **p** wordt **p** geschat met:

- **Relatieve frequentie:**
  $$\hat{P} = \frac{1}{n} \sum\_{i=1}^{n} X_i$$
  Dit is een onvertekende schatter van **p**.
- **Variantie:**
  $$Var(\hat{P}) = \frac{p(1-p)}{n}$$
  Hoe groter **n**, hoe kleiner de variantie.

**Benadering met de Centrale Limietstelling:**
$$\frac{\hat{P} - p}{\sqrt{p(1-p)/n}} \approx N(0,1)$$

## 3.3 **Belangrijkste Kernpunten**

- **Steekproefgemiddelde (X̄n) is een schatter voor populatiegemiddelde (µ).**
- **CLS: Voor grote n wordt het gemiddelde normaal verdeeld.**
- **Een goede schatter is onvertekend, heeft minimale variantie en lage MSE.**
- **Voor een normale populatie is X̄n de beste schatter van µ en S² de beste schatter van σ².**
- **Bij Bernoulli-variabelen is $\hat{P}$ een schatter voor de kans p.**
