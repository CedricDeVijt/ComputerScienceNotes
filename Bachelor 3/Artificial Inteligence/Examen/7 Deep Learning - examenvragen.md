## 1 Backpropagation

### 1.1 Wat is backpropagation? Wat problemen lost het op?

Backpropagation, kort voor "backward propagation of errors," is een algoritme dat wordt gebruikt om de gewichten in een neuraal netwerk te optimaliseren. Het speelt een cruciale rol in het trainen van deep learning modellen. Het werkt door fouten (loss) van de uitvoerlaag terug te sturen naar eerdere lagen, zodat het netwerk kan leren welke gewichten moeten worden aangepast.

**Problemen die het oplost:**

- **Effectieve gewichtsoptimalisatie:** Door gebruik te maken van de kettingregel kan backpropagation bepalen hoe elk gewicht in het netwerk bijdraagt aan de fout.
- **Efficiëntie:** Het maakt het trainen van diepe neurale netwerken praktisch mogelijk, zelfs met veel parameters.
- **Automatisering:** Door gradienten automatisch te berekenen, vermindert het de noodzaak voor handmatig afgeleiden af te leiden.

Backpropagation is een fundamenteel onderdeel van de meeste moderne gradient-descent-algoritmen zoals Stochastic Gradient Descent (SGD) en Adam.

## 2 Neural Networks

### 2.1 Convolutional Neural Networks

#### 2.1.1 Wat is een convolutional layer? Geef een voorbeeld.

Een convolutional layer is een kerncomponent van een Convolutional Neural Network (CNN). Het voert convolutie-operaties uit op de inputdata (zoals afbeeldingen), waarbij kenmerken worden geëxtraheerd door kleine, schuivende filters (ook wel kernels genoemd). Deze filters detecteren patronen zoals randen, hoeken en texturen.

**Voorbeeld:**

- Input: Een afbeelding van 28x28 pixels.
- Kernel: Een 3x3 filter dat randen detecteert.
- Output: Een feature map, bijvoorbeeld 26x26 pixels, die de randen in de afbeelding vertegenwoordigt.

De uitvoer van een convolutional layer wordt vaak doorgegeven aan een activatiefunctie zoals ReLU om niet-lineariteit te introduceren. Daarna volgen meestal pooling layers voor downsampling.

### 2.2 Overfitting in Neural Networks

#### Wat is overfitting en welke technieken zijn er om dit tegen te gaan?

Overfitting treedt op wanneer een neuraal netwerk de trainingsdata te goed leert, inclusief ruis en irrelevante patronen. Dit leidt tot een slechte generalisatie naar nieuwe, onzichtbare data.

**Tekenen van overfitting:**

- Hoge nauwkeurigheid op de trainingsdata, maar lage nauwkeurigheid op de validatie- of testdata.

**Technieken om overfitting tegen te gaan:**

1. **Meer data verzamelen:** Meer gevarieerde trainingsdata vermindert de kans dat het netwerk zich beperkt tot specifieke patronen in de dataset.
2. **Regularisatie:**
   - L1/L2 regularisatie voegt een strafterm toe aan het verlies om grote gewichten te voorkomen.
3. **Dropout:** Een techniek waarbij willekeurige neuronen tijdens training worden uitgeschakeld om over-afhankelijkheid te verminderen.
4. **Data Augmentatie:** Kunstmatig vergroten van de dataset door transformaties zoals roteren, spiegelen en schalen.
5. **Vroegtijdig stoppen:** Training stoppen wanneer de validatiefout niet meer verbetert.
6. **Batch Normalisatie:** Het stabiliseert de training door normalisatie van inputs binnen lagen.

Door deze technieken toe te passen, wordt een netwerk robuuster en kan het beter generaliseren naar nieuwe data.
