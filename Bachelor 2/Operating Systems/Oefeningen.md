# Caching

## Een 64KiB, direct mapped cache heeft 16 byte blocks. Je mag veronderstellen dat het geheugen byte geadresseerd is (dus 1 woord = 1 byte). Als adressen 32 bits lang zijn, hoeveel bits zijn er dan voorzien voor de tag, de index, en de oﬀset in deze cache?

Laten we het probleem stap voor stap oplossen.

### 1. **Gegeven informatie**:

- Cachegrootte: \( 64 \, \text{KiB} = 64 \times 1024 = 65{,}536 \, \text{bytes} \)
- Blokgrootte: \( 16 \, \text{bytes per blok} \)
- Adreslengte: \( 32 \, \text{bits} \)
- Cache is **direct mapped**.

### 2. **Berekeningen**:

#### a. **Aantal blokken in de cache**:

\[
\text{Aantal blokken} = \frac{\text{Cachegrootte}}{\text{Blokgrootte}} = \frac{65{,}536}{16} = 4{,}096 \, \text{blokken}.
\]

#### b. **Aantal bits voor de offset**:

De offset bepaalt welk byte binnen een blok wordt aangesproken. Omdat elk blok \( 16 \, \text{bytes} \) bevat, zijn er:
\[
\text{Offset-bits} = \log_2(16) = 4 \, \text{bits}.
\]

#### c. **Aantal bits voor de index**:

De index bepaalt welk blok in de cache wordt aangesproken. Met \( 4{,}096 \) blokken zijn er:
\[
\text{Index-bits} = \log_2(4{,}096) = 12 \, \text{bits}.
\]

#### d. **Aantal bits voor de tag**:

De tag identificeert of een bepaald geheugenadres in de cache staat. Het aantal tag-bits wordt bepaald door het totale aantal adresbits (\( 32 \)) minus de offset- en index-bits:
\[
\text{Tag-bits} = 32 - (\text{Index-bits} + \text{Offset-bits}) = 32 - (12 + 4) = 16 \, \text{bits}.
\]

### 3. **Samenvatting**:

- **Offset**: \( 4 \, \text{bits} \)
- **Index**: \( 12 \, \text{bits} \)
- **Tag**: \( 16 \, \text{bits} \)

### Adresindeling:

Het 32-bits geheugenadres wordt als volgt opgedeeld:
\[
\text{[Tag (16 bits)] [Index (12 bits)] [Offset (4 bits)]}
\]

## Pas je antwoord aan indien de cache 4-way set associatief is in plaats van direct.

Als de cache **4-way set associatief** is, verandert de manier waarop de cache wordt georganiseerd. Laten we de berekeningen herzien.

---

### 1. **Gegeven informatie**:

- Cachegrootte: \( 64 \, \text{KiB} = 65{,}536 \, \text{bytes} \)
- Blokgrootte: \( 16 \, \text{bytes per blok} \)
- Adreslengte: \( 32 \, \text{bits} \)
- **4-way set associatieve cache**.

---

### 2. **Berekeningen**:

#### a. **Aantal blokken in de cache**:

De totale cachegrootte en blokgrootte zijn onveranderd, dus:
\[
\text{Aantal blokken} = \frac{\text{Cachegrootte}}{\text{Blokgrootte}} = \frac{65{,}536}{16} = 4{,}096 \, \text{blokken}.
\]

#### b. **Aantal sets in de cache**:

In een 4-way set associatieve cache worden de blokken verdeeld over sets, met \( 4 \) blokken per set. Het aantal sets wordt:
\[
\text{Aantal sets} = \frac{\text{Aantal blokken}}{\text{Aantal associatieve wegen}} = \frac{4{,}096}{4} = 1{,}024 \, \text{sets}.
\]

#### c. **Aantal bits voor de offset**:

De offset bepaalt welk byte binnen een blok wordt aangesproken. Dit is hetzelfde als bij de direct mapped cache:
\[
\text{Offset-bits} = \log_2(\text{Blokgrootte}) = \log_2(16) = 4 \, \text{bits}.
\]

#### d. **Aantal bits voor de index**:

De index bepaalt naar welke set in de cache wordt verwezen. Aangezien er \( 1{,}024 \) sets zijn:
\[
\text{Index-bits} = \log_2(\text{Aantal sets}) = \log_2(1{,}024) = 10 \, \text{bits}.
\]

#### e. **Aantal bits voor de tag**:

De tag identificeert welk blok in het geheugen overeenkomt met een cacheblok. Het aantal tag-bits wordt bepaald door het totale aantal adresbits (\( 32 \)) minus de offset- en index-bits:
\[
\text{Tag-bits} = 32 - (\text{Index-bits} + \text{Offset-bits}) = 32 - (10 + 4) = 18 \, \text{bits}.
\]

---

### 3. **Samenvatting**:

- **Offset**: \( 4 \, \text{bits} \)
- **Index**: \( 10 \, \text{bits} \)
- **Tag**: \( 18 \, \text{bits} \)

---

### Adresindeling:

Het 32-bits geheugenadres wordt nu als volgt opgedeeld:
\[
\text{[Tag (18 bits)] [Index (10 bits)] [Offset (4 bits)]}
\]

## Hoeveel bits hebben we voor de index nodig indien de cache volledig associatief is? Verklaar je antwoord.

In een **volledig associatieve cache** zijn er **geen sets of indices**. Elk blok in de cache kan worden toegewezen aan elk geheugenadres, zonder beperkingen van een index. Laten we dit uitleggen en berekenen:

---

### 1. **Gegeven informatie**:

- Cachegrootte: \( 64 \, \text{KiB} = 65{,}536 \, \text{bytes} \)
- Blokgrootte: \( 16 \, \text{bytes per blok} \)
- Adreslengte: \( 32 \, \text{bits} \)
- Cache is **volledig associatief**.

---

### 2. **Volledig associatieve cache**:

In een volledig associatieve cache zijn **alle blokken onderdeel van één grote set**. Hierdoor is er **geen aparte index nodig om een set te selecteren**. De bits van het geheugenadres worden als volgt verdeeld:

#### a. **Offset-bits**:

De offset bepaalt welk byte binnen een blok wordt aangesproken. Dit is hetzelfde als in andere configuraties:
\[
\text{Offset-bits} = \log_2(\text{Blokgrootte}) = \log_2(16) = 4 \, \text{bits}.
\]

#### b. **Geen index**:

Omdat alle blokken deel uitmaken van één grote set, hebben we geen index nodig:
\[
\text{Index-bits} = 0.
\]

#### c. **Tag-bits**:

De rest van het adres wordt gebruikt voor de tag, om unieke geheugenadressen te identificeren. Het aantal tag-bits is dus:
\[
\text{Tag-bits} = 32 - (\text{Index-bits} + \text{Offset-bits}) = 32 - (0 + 4) = 28 \, \text{bits}.
\]

---

### 3. **Samenvatting**:

- **Offset**: \( 4 \, \text{bits} \)
- **Index**: \( 0 \, \text{bits} \)
- **Tag**: \( 28 \, \text{bits} \)

---

### Verklaring:

In een volledig associatieve cache wordt de gehele cache beschouwd als één grote set. Daarom is er geen noodzaak voor een index om een specifieke set te selecteren, en alle bits behalve de offset worden toegewezen aan de tag.
