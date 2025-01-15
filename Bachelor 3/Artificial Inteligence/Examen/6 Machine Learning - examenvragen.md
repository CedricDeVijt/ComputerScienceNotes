## 1 Overfitting

### 1.1 Wat is overfitting? Hoe kunnen we testen of een classifier overfitted?

Overfitting treedt op wanneer een machine learning-model te goed leert op de trainingsdata, inclusief ruis en irrelevante details, waardoor het slecht generaliseert naar nieuwe, ongeziene data. Dit betekent dat het model uitzonderlijk goed presteert op de trainingsset, maar slecht presteert op de testset of in de praktijk.

Om te testen of een classifier overfitted is, kunnen we de volgende methoden gebruiken:

- **Train-Test Split:** Splits de dataset in trainings- en testgegevens. Vergelijk de prestaties op beide datasets.
- **Cross-Validation:** Gebruik k-fold cross-validation om consistentie te evalueren over verschillende splitsingen van de data.
- **Learning Curves:** Analyseer de trainings- en validatiefouten naarmate het aantal trainingsvoorbeelden toeneemt. Bij overfitting blijft de trainingsfout laag, terwijl de validatiefout hoog is.

### 1.2 Hoe kunnen we overfitting tegengaan?

Om overfitting te voorkomen, kun je de volgende technieken toepassen:

- **Regularisatie:** Voeg een regulatieterm toe aan de verliesfunctie, zoals L1- of L2-regularisatie.
- **Meer data verzamelen:** Een groter trainingsdataset vermindert de kans op overfitting.
- **Feature selectie:** Verwijder irrelevante of sterk gecorreleerde kenmerken uit de dataset.
- **Dropout:** Gebruik dropout in neurale netwerken om willekeurige neuronen tijdens training uit te schakelen.
- **Vroege stopzetting:** Stop het trainingsproces zodra de prestaties op een validatieset niet meer verbeteren.
- **Verminder modelcomplexiteit:** Gebruik een eenvoudiger model met minder parameters.

## 2 Naive Bayes

### 2.1 Maak een Naive Bayes classifier voor een dataset en gebruik deze om de kans te berekenen dat een bepaalde observatie tot een bepaalde klasse behoort

Een Naive Bayes classifier is gebaseerd op de Bayesiaanse regel:

$$
P(C|X) = \frac{P(X|C)P(C)}{P(X)}
$$

waarbij:

- $P(C|X)$ de kans is dat de observatie X behoort tot klasse C (posterior probability).
- $P(X|C)$ de kans is op de waargenomen gegevens X, gegeven klasse C (likelihood).
- $P(C)$ de a priori-kans van klasse C.
- $P(X)$ de totale kans op de observatie X.

Stappen om een Naive Bayes classifier te gebruiken:

1. **Train de classifier:** Bereken $P(C)$ en $P(X|C)$ op basis van de trainingsdata.
2. **Bereken posteriors:** Gebruik de formule om de posterior probability te berekenen voor elke klasse.
3. **Classificeer:** Kies de klasse met de hoogste posterior probability.

### 2.2 Wat is smoothing in Naive Bayes? Waarom is dit nodig?

Smoothing wordt gebruikt om problemen met nulwaarschijnlijkheden te vermijden, die optreden wanneer een bepaalde combinatie van kenmerken en klassen niet voorkomt in de trainingsdata. Zonder smoothing zou $P(X|C)$ nul worden, waardoor het gehele product in de formule nul wordt.

Een populaire smoothingtechniek is **Laplace smoothing**, waarbij we een kleine constante toevoegen aan de teller en de noemer:

$$
P(X|C) = \frac{n\_{X,C} + \alpha}{n_C + \alpha |V|}
$$

waarbij:

- $n\_{X,C}$ het aantal keren is dat X voorkomt in klasse C.
- $n_C$ het totale aantal waarnemingen in klasse C.
- $\alpha$ de smoothing-parameter (bijvoorbeeld 1).
- $|V|$ de grootte van de uitkomstruimte van X.

Smoothing zorgt voor robuustere prestaties, vooral bij kleine datasets.

## 3 Decision Trees

### 3.1 Wat is een decision tree?

Een decision tree is een hiërarchische modelstructuur die beslissingen neemt door de gegevens in een boomvorm te splitsen op basis van kenmerken. Elke interne knoop vertegenwoordigt een splitsing op een kenmerk, elke tak een uitkomst van die splitsing, en elk blad een klasse of voorspelling.

Voordelen van decision trees:

- Ze zijn eenvoudig te begrijpen en te visualiseren.
- Ze kunnen zowel numerieke als categorische gegevens verwerken.
- Ze vereisen weinig gegevensvoorbewerking.

### 3.2 Hoe kunnen we een decision tree opstellen?

Een decision tree wordt opgebouwd door herhaaldelijk de trainingsdata te splitsen op een manier die de informatieverliezen minimaliseert. Veelgebruikte criteria zijn:

- **Information Gain (IG):** Gebaseerd op entropie, meet IG de reductie in onzekerheid.
- **Gini-index:** Een maatstaf voor onzuiverheid in een dataset.

Stappen om een decision tree te bouwen:

1. **Splitscriterium kiezen:** Bepaal het kenmerk waarop gesplitst moet worden op basis van IG, Gini-index of een ander criterium.
2. **Splitsing uitvoeren:** Verdeel de data in subsets volgens de waarden van het kenmerk.
3. **Herhaling:** Herhaal stap 1 en 2 recursief op elke subset.
4. **Stopconditie:** Stop splitsingen wanneer:
   - Een vooraf ingestelde boomhoogte is bereikt.
   - Een minimale grootte van de dataset per knoop is bereikt.
   - De data volledig homogeen is (alle observaties behoren tot dezelfde klasse).

Praktische implementaties maken vaak gebruik van bibliotheken zoals scikit-learn in Python.
