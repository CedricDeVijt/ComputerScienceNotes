## 1 Geef het efficiëntste algoritme voor het implementeren van een AI-speler voor een spel

### 1.1 Mens erger je niet

Voor "Mens erger je niet" (een bordspel met een sterk stochastisch element door het gebruik van dobbelstenen), is een directe berekening van alle mogelijke zetten niet praktisch. In plaats daarvan:
**Algoritme:** Monte Carlo Tree Search (MCTS).

- **Waarom:** MCTS is geschikt voor spellen met een grote toestandsruimte en stochastische elementen zoals dobbelstenen. Het zoekt stochastisch door de toestandsruimte en selecteert acties gebaseerd op simulaties.
- **Hoe:**
  1. Voer simulaties uit vanuit de huidige toestand.
  2. Gebruik het **Upper Confidence Bound for Trees (UCT)**-criterium om tussen zetten te kiezen.
  3. Verfijn de simulaties naarmate meer informatie beschikbaar wordt.

### 1.2 Nim (2 spelers, 6 stokjes)

**Algoritme:** Optimalisatie via winnende configuraties.

- **Waarom:** Nim heeft een bekende wiskundige oplossing gebaseerd op de **Nim-som** (XOR van stapelgroottes). Voor een AI-speler is het voldoende om deze regel toe te passen.
- **Hoe:**
  1. Bereken de Nim-som van de huidige stapels.
  2. Indien de Nim-som $\neq$ 0, maak een zet zodat de Nim-som = 0.
  3. Indien de Nim-som = 0, speel willekeurig (verlies is gegarandeerd als de tegenstander foutloos speelt).

### 1.3 Nim (3 spelers, 6 stokjes)

**Algoritme:** Uitgebreide analyse van winnende configuraties.

- **Waarom:** Voor meerdere spelers zijn de optimale zetten afhankelijk van zowel de huidige toestand als de volgorde van spelers. De analyse wordt complexer, maar winnende strategieën blijven toepasbaar via generalisaties van de Nim-som.
- **Hoe:**
  1. Stel een **coalitie-systeem** op waarin je de winstkansen per speler bepaalt.
  2. Maak zetten die je eigen winstkans maximaliseren en/of de kansen van anderen minimaliseren.
  3. Gebruik simulatie of een aangepaste vorm van MCTS om te anticiperen op meerdere tegenstanders.

### 1.4 Nim met muntopgooien (kop = 1 extra stokje)

**Algoritme:** Stochastische dynamische programmering.

- **Waarom:** De munt introduceert een stochastisch element. Dynamische programmering kan hier omgaan met de onzekerheid van extra stokjes.
- **Hoe:**
  1. Modelleer de speltoestand als een Markov Decision Process (MDP).
  2. Bereken de verwachte waarde van elke mogelijke zet met behulp van probabilistische uitkomsten van de munt.
  3. Maak zetten die de verwachte waarde maximaliseren.

### 1.5 Schaken

**Algoritme:** Minimax met Alpha-Beta Pruning.

- **Waarom:** Schaken is deterministisch en heeft een enorme toestandsruimte. Minimax optimaliseert de zetten door te proberen de score te maximaliseren (voor jezelf) en te minimaliseren (voor de tegenstander), terwijl alpha-beta pruning onnodige takken snoeit.
- **Hoe:**
  1. Beperk de zoekdiepte (bijv. 5-10 zetten vooruit afhankelijk van rekenkracht).
  2. Gebruik een **heuristiek** zoals materiële balans, koningveiligheid, en pionstructuur.
  3. Voeg eventueel **transpositietabellen** en **iteratieve verdieping** toe om efficiëntie te verhogen.

### 1.6 Tic-tac-toe

**Algoritme:** Minimax (volledige zoekruimte).

- **Waarom:** Tic-tac-toe heeft een kleine toestandsruimte (slechts 9 velden), waardoor een volledige zoekruimte mogelijk is. Minimax biedt een gegarandeerde optimale strategie.
- **Hoe:**
  1. Bepaal alle mogelijke zetten en hun uitkomsten.
  2. Kies de zet die leidt tot winst of een gegarandeerd gelijkspel.
  3. Geen verdere optimalisaties nodig vanwege de eenvoudige aard van het spel.
