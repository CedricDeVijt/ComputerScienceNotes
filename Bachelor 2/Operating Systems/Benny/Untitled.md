# Cache Geheugen: Een Studiehandleiding

## Hoofdstuk 1: Overzicht van Computergeheugen

### Interne en Externe Geheugen
- **Interne geheugen** omvat:
  - Registers in de processor
  - **Cache geheugen**
  - Main memory (RAM)
  - Eigenschappen: Vaak volatiel, verliest data zonder stroom.
- **Externe geheugen** omvat:
  - Disks
  - Flash geheugen
  - Tapes

### Geheugenhiërarchie
- Soorten geheugen georganiseerd in een hiërarchie:
  1. **Prijs per bit** neemt af naarmate we naar lager niveau gaan.
  2. **Omvang** van het geheugen neemt toe.
  3. **Toegangstijd** neemt toe.
  4. **Frequentie van toegang** door de processor neemt af.

- Belangrijk concept: **Locality of Reference**
  - Tijdelijke herhaling in data-/instructietoegang (bijv. in lussen).
  - Nabijheid van data-instructies verhoogt waarschijnlijkheid van toegang.

### Kerngetallen
- Cache: Enkele Kbytes tot enkele Mbytes.
- Main Memory: Enkele Gbytes.
- Disks: Enkele Tbytes.
- Access times:
  - Cache: Nanoseconden (40x sneller dan main memory).
  - Main memory: 10.000x sneller dan disks (milliseconden).

---

## Hoofdstuk 2: Organisatie van Cache Geheugen

### Basisstructuur
- **Cache geheugen**:
  - Meestal **on-chip** (dicht bij processor).
  - Verbindt via **snelle bus** met processor.
  - Traag geheugen (main memory) verbonden via gedeelde bus.

### Cache Functie
- Cache bevat een **deelverzameling** van main memory.
- Organisatie:
  - Main memory verdeeld in **blokken** (K woorden).
  - Cache heeft **lijnen** met:
    - Tag: Identificeert blokken.
    - Data: Woorden uit blokken.
    - Control bits (bijv. "In Use", "UPDATE").

### Cache Hits en Misses
- **Hit**: Gevraagde woord direct beschikbaar in cache.
- **Miss**: Blok geladen van main memory naar cache.
  - **Hit ratio**: Kans dat woord in cache is.

---

### Direct Mapping
- Elk blok in main memory mapt op een unieke lijn in cache.
  - Formule: `i = j mod 2^r`
  - `i`: Cache lijnnummer
  - `j`: Bloknummer

#### Voordelen
- Simpele implementatie.

#### Nadelen
- **Thrashing**: Herhaald overschrijven van blokken door conflicts in mapping.

### Associative Mapping
- Blokken kunnen overal in cache worden geplaatst.
  - **Voordelen**: Geen vaste locatie; voorkomt thrashing.
  - **Nadelen**: Complex en duur; langere tags nodig.

### Set-Associative Mapping
- Cache verdeeld in "sets"; blokken beperkt tot een specifieke set.
  - **k-way set-associative cache**:
    - Combineert voordelen van direct en associative mapping.
    - Kleine waarden voor `k` (bijv. 2, 4, 8) gebruikelijk.

#### Voordelen
- Vermijdt thrashing.
- Minder complex dan associative mapping.

#### Nadelen
- Minder flexibel dan associative mapping.

### Replacement Algoritmen
- **Least Recently Used (LRU)**
  - Verwijdert minst recent gebruikte blok.
  - Vereist extra opslag voor tracking.

- **First In First Out (FIFO)**
  - Verwijdert oudste blok.
  - Eenvoudige implementatie met cirkelbuffer.

- **Pseudo LRU (PLRU)**
  - Varianten: Tree-based (TB) en Most Recently Used (MRU).
  - Snellere implementatie van LRU.

---

## Hoofdstuk 3: Geheugenupdates: Write Policy

### Write-Through
- Elke update direct doorgevoerd naar main memory.
- **Nadeel**: Veel verkeer op de bus.

### Write-Back
- Update alleen doorgevoerd naar main memory als blok wordt verwijderd.
  - UPDATE-bit: Geeft aan of data verschilt van main memory.

---

## Hoofdstuk 4: Aantal Caches in Hedendaagse Systemen

### Cache Levels
- **L1 Cache**: Klein, snel (bijv. 32 Kbyte, ~4 cycles).
- **L2 Cache**: Groter, trager (bijv. 256 Kbyte).
- **L3 Cache**: Gedeeld, grootste en traagste (meerdere Mbytes).

### Inclusieve vs. Exclusieve Caches
- **Inclusieve**: Inhoud L1 cache ook in L2.
- **Exclusieve**: Data bevindt zich slechts in één cache.

### Split Cache
- Gescheiden caches voor data en instructies.
- Voordelen:
  - Parallelle toegang mogelijk.
  - **Prefetching**: Toekomstige data/instructies laden.

---

## Hoofdstuk 5: Cache Benchmarking

### Testmethode
- Arrays van verschillende groottes doorlopen met verschillende strides.
- Plot gemiddelde toegangstijd als functie van stride.

### Resultaten
- **L1 Cache Grootte**: 128 Kbyte.
- **Extra Rekentijd bij L1 Miss**: ~425 nanoseconden.
- **Cache Associativiteit**: 4-way associatief.
- **Geen L2 Cache** geobserveerd in resultaten.
- **TLB Page Size**: 16 Kbytes.

---

## Belangrijkste Concepten

- **Cache Geheugen**: Snel, klein geheugen dicht bij processor.
- **Geheugenhiërarchie**: Organisatie in lagen gebaseerd op snelheid en kosten.
- **Mapping Methodes**:
  - Direct: Simpel maar conflictgevoelig.
  - Associative: Flexibel maar duur.
  - Set-Associative: Balans tussen eenvoud en flexibiliteit.
- **Locality of Reference**: Basis voor cache-efficiëntie.
- **Write Policy**:
  - Write-through: Directe updates.
  - Write-back: Updates bij cache-verwijdering.

### Cache Specificaties
- **Hit Ratio**: Belangrijk voor prestaties.
- **Replacement Algoritmen**: Optimaliseren gebruik van beperkte cache-ruimte.
- **Benchmarks**: Evalueren cache eigenschappen zoals grootte en associativiteit.

Met deze handleiding kun je snel essentiële concepten en feiten over cache geheugen herzien en toepassen.

