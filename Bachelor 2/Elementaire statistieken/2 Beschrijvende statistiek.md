## 2.1 Inleiding tot Beschrijvende Statistiek en EDA

- **Beschrijvende statistiek**: Richt zich op het samenvatten en visueel weergeven van gegevens via tabellen en grafieken (bijv. histogrammen, staafdiagrammen).
- **Exploratieve Data Analyse (EDA)**: Moderne methode (sinds 1970) om patronen en structuren te detecteren met computergestuurde visualisaties (QQ-plot, boxplot).
  Divisionele focus: Analyseert steekproeven uit populaties vanwege praktische beperkingen (tijd, kosten, onmogelijkheid om volledige populaties te meten).

## 2.2 Typen Variabelen en Dataverzameling

### Kwalitatieve Variabelen

- **Nominale variabelen**: Categorieën zonder rangorde (bijv. geslacht, nationaliteit).
- **Ordinale variabelen**: Categorieën met rangorde (bijv. opleidingsniveau, productkwaliteit).

### Kwantitatieve Variabelen

- Numerieke waarden waarvoor rekenkundige bewerkingen zinvol zijn (bijv. leeftijd, snelheid).
- **Continu**: Oneindig aantal mogelijke waarden (bijv. lengte).
- **Discreet**: Eindige of telbare waarden (bijv. aantal kinderen).

## 2.3 Frequentieverdelingen en Grafische Voorstellingen

### Frequentietabellen en Staafdiagrammen

- **Absolute frequentie** ($nj$): Aantal observaties per categorie.
- **Relatieve frequentie** ($hj = nj/n$): Proportie per categorie.
- **Voorbeeld**: 60 steden verdeeld over 5 regio’s met relatieve frequenties in een staafdiagram.

### Histogrammen voor Kwantitatieve Data

- **Klassenindeling**: Groepeer data in intervallen (bijv. snelheden in klassen van 5 km/u).
- **Klassenmidden** ($cj$): Middenpunt van elk interval.
- **Dichtheidshistogram**: Hoogte = $hj / klassebreedte$ om vertekening bij ongelijke breedtes tegen te gaan.

## 2.4 Centrum- en Spreidingsmaten

### Centrummaten

1. **Gemiddelde** ($x̄$):
   $x̄ = (Σxi) / n$ of $x̄ = (Σnjcj) / n$ voor gegroepeerde data.
2. **Mediaan**: Middelste waarde na ordening; bij even $n$: gemiddelde van twee middelste waarden.
3. **Modus**: Meest voorkomende waarde of klasse (modale klasse).

### Spreidingsmaten

1. **Variantie** ($s^2$):
   $s^2 = Σ(xi - x̄)^2 / (n-1)$ voor ruwe data; $Σnj(cj - x̄)^2 / (n-1)$ voor gegroepeerde data.
2. **Standaardafwijking** ($s$): $s = \sqrt{s^2}$.
3. **Interkwartielafstand (IQR)**:
   $IQR = Q3 - Q1$ (verschil tussen 75e en 25e percentiel).
4. **MAD**: Mediaan van absolute afwijkingen t.o.v. mediaan.

## 2.5 Grafische Technieken voor Data-analyse

### Boxplot (Tukey, 1977)

- Visualiseert mediaan, kwartielen, IQR en uitschieters.
- **Uitschieters**: Waarnemingen buiten $[Q1 - 1.5×IQR, Q3 + 1.5×IQR]$.
- **Interpretatie**: Symmetrie, staartgedrag en spreiding.

### Scatterplot en Correlatie

- **Scatterplot**: Toont verband tussen twee kwantitatieve variabelen.
- **Pearson-correlatie** ($r$): Meet lineair verband (-1 ≤ $r$ ≤ 1).

### Kruistabellen voor Kwalitatieve Data

- Tabel met frequenties per combinatie van categorieën (bijv. regio vs. inkomensklasse).
- Analyse van onafhankelijkheid via verwachte vs. geobserveerde frequenties.

### QQ-plot

- Vergelijkt empirische kwantielen met theoretische (bijv. normale verdeling).
- **Normaliteitstest**: Punten op een rechte lijn suggereren normaliteit.

---

## Key Points to Remember

- **Steekproef vs. Populatie**: Steekproef moet representatief zijn voor betrouwbare conclusies.
- **Klassenindeling**: Kies 5–20 klassen; voorkom te piekige of vlakke histogrammen.
- **Gemiddelde vs. Mediaan**: Mediaan robuuster bij scheve data.
- **Variantie & Standaardafwijking**: Meet spreiding t.o.v. gemiddelde.
- **Correlatie≠Causaliteit**: Correlatie wijst op associatie, niet noodzakelijk oorzakelijk verband.
- **QQ-plot**: Hulpmiddel om verdeling (bv. normaliteit) visueel te beoordelen.
