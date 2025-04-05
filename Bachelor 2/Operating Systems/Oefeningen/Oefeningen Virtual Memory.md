# 2 Virtual Memory

## Buddy system

In een buddy-systeem is het geheugen georganiseerd in blokken van grootte $2^n$, waarbij $n$ een positieve integer is. Elke keer dat een geheugenaanvraag wordt gedaan, wordt een blok toegewezen dat de dichtstbijzijnde macht van 2 is die de gevraagde grootte kan accommoderen. Als het blok later wordt vrijgegeven, wordt het gecombineerd met zijn "buddy" (het blok van dezelfde grootte waarmee het is gekoppeld), indien mogelijk, om grotere vrije blokken te creëren.

## Paging

### 1 Omvang van de page tables van een proces

Stel dat we een 32-bit machine hebben met virtuele adressen die zijn opgesplitst in 4 delen van 10, 8, 6 en 8 bits respectievelijk. We hanteren deze adressen in een 3 level page table systeem, waarbij de eerste 10 bits gebruikt worden voor level 1, de volgende 8 bits voor level 2, etc. Een enkele page table entry is 4 bytes groot. Het systeem is byte geaddresseerd.

1. Wat is de page size in dit systeem?
   We kunnen de page size berekenen door te kijken naar de laatste set van bits in de virtuele adresstructuur, omdat deze bepalen hoeveel bytes er per pagina zijn.

In dit geval is de adresstructuur als volgt opgesplitst:

- **Level 1**: 10 bits (index in de eerste page table)
- **Level 2**: 8 bits (index in de tweede page table)
- **Level 3**: 6 bits (index in de derde page table)
- **Offset**: 8 bits (offset binnen een pagina)

De **offset** bepaalt de grootte van een pagina. Met 8 bits kunnen we $2^8$ verschillende offsets adresseren. Dit betekent dat de pagina grootte:

$$
\text{Page size} = 2^{8} = 256 \text{ bytes.}
$$

De page size is **256 bytes**.

2. Stel dat een process 256K geheugen vereist (dat start vanaf adres 0), hoeveel plaats
   nemen de page tables van dit proces dan in beslag?

Laten we dit stap voor stap uitwerken:

Gegeven informatie:

1. Het proces vereist **256 KB** geheugen, wat overeenkomt met $256 \times 1024 = 2^{18}$ bytes.
2. De page size is $256$ bytes ($2^8$).
3. Een enkele **page table entry (PTE)** is $4$ bytes groot.
4. Het systeem gebruikt een **3-level page table** waarbij de virtuele adressen zijn opgesplitst in 10, 8, 6, en 8 bits.

Aantal pagina's:

Elke pagina is 256 bytes groot. Het aantal benodigde pagina's is:

$$
\text{Aantal pagina's} = \frac{\text{Totale grootte}}{\text{Page size}} = \frac{2^{18}}{2^8} = 2^{10} = 1024 \text{ pagina's.}
$$

Het proces heeft dus **1024 pagina's** nodig.

Structuur van de page tables:

We analyseren hoe de page tables georganiseerd zijn over de 3 levels:

1. **Level 3:**

   - Elke Level 3 tabel bevat $2^6 = 64$ entries, omdat dit niveau 6 bits gebruikt.
   - Om 1024 pagina's te adresseren, hebben we:
     $$
     \text{Aantal benodigde Level 3 tabellen} = \frac{\text{Aantal pagina's}}{\text{Entries per Level 3 tabel}} = \frac{1024}{64} = 16.
     $$
   - Elke Level 3 tabel neemt $64 \times 4 = 256$ bytes in beslag.
   - De totale ruimte voor Level 3 tabellen is:
     $$
     \text{Ruimte Level 3 tabellen} = 16 \times 256 = 4096 \text{ bytes (4 KB).}
     $$

2. **Level 2:**

   - Elke Level 2 tabel bevat $2^8 = 256$ entries, omdat dit niveau 8 bits gebruikt.
   - Om de 16 Level 3 tabellen te adresseren, hebben we:
     $$
     \text{Aantal benodigde Level 2 tabellen} = \frac{\text{Aantal Level 3 tabellen}}{\text{Entries per Level 2 tabel}} = \frac{16}{256} = 1.
     $$
   - Elke Level 2 tabel neemt $256 \times 4 = 1024$ bytes in beslag.
   - De totale ruimte voor Level 2 tabellen is:
     $$
     \text{Ruimte Level 2 tabellen} = 1024 \text{ bytes (1 KB).}
     $$

3. **Level 1:**
   - Elke Level 1 tabel bevat $2^{10} = 1024$ entries, omdat dit niveau 10 bits gebruikt.
   - Er is slechts één Level 1 tabel nodig om de ene Level 2 tabel te adresseren.
   - De Level 1 tabel neemt $1024 \times 4 = 4096$ bytes in beslag.
   - De totale ruimte voor de Level 1 tabel is:
     $$
     \text{Ruimte Level 1 tabel} = 4096 \text{ bytes (4 KB).}
     $$

Totale ruimte voor page tables:

De totale ruimte die nodig is voor alle page tables is de som van de ruimte van de drie levels:

$$
\text{Totale ruimte} = \text{Level 1 ruimte} + \text{Level 2 ruimte} + \text{Level 3 ruimte}.
$$

$$
\text{Totale ruimte} = 4096 + 1024 + 4096 = 9216 \text{ bytes.}
$$

**Antwoord:**

De page tables nemen in totaal **9216 bytes (9 KB)** in beslag.

3. Stel dat een proces een code segment heeft van 48K vanaf (virtueel) adres 0x10000000, een 600K data segment vanaf adres 0x80000000 en een stack segment van 64K vanaf adres 0xF0000000. Hoeveel plaats vereist de page table van dit proces?

Laten we stap voor stap nagaan hoe de oplossing tot stand komt:

Gegevens:

1. Virtueel adres is opgesplitst in:

   - Level 1: **10 bits**,
   - Level 2: **8 bits**,
   - Level 3: **6 bits**,
   - Offset: **8 bits**.

2. Page size = $256$ bytes ($2^8$).

3. Page table entries (PTE) zijn $4$ bytes groot.

4. **Code segment:**

- **Startadres:** $0x10000000$
- **Grootte:** $48 \, \text{KB}$.

Berekeningen:

- Aantal pagina's:

  $$
  \text{Aantal pagina's} = \frac{\text{Grootte}}{\text{Page size}} = \frac{48 \times 1024}{256} = 192.
  $$

- Aantal benodigde **Level 3 tables**:

  - Elke Level 3 tabel bevat $64$ entries ($2^6$).
  - Aantal Level 3 tables:
    $$
    \frac{192}{64} = 3 \, \text{(afronden naar boven)}.
    $$

- Aantal benodigde **Level 2 tables**:

  - Elke Level 2 tabel bevat $256$ entries ($2^8$).
  - Aantal Level 2 tables:
    $$
    \frac{3}{256} = 1 \, \text{(slechts 1 Level 2 tabel nodig)}.
    $$

- Aantal benodigde **Level 1 tables**:
  - Slechts 1 Level 1 tabel nodig omdat alle 192 pagina's binnen dezelfde Level 1 range vallen.

2. **Data segment:**

- **Startadres:** $0x80000000$
- **Grootte:** $600 \, \text{KB}$.

Berekeningen:

- Aantal pagina's:

  $$
  \text{Aantal pagina's} = \frac{\text{Grootte}}{\text{Page size}} = \frac{600 \times 1024}{256} = 2400.
  $$

- Aantal benodigde **Level 3 tables**:

  $$
  \frac{2400}{64} = 37.5 \, \Rightarrow \, 38 \, \text{(afronden naar boven)}.
  $$

- Aantal benodigde **Level 2 tables**:

  - Elke Level 2 tabel bevat $256$ entries ($2^8$).
    $$
    \frac{38}{256} = 1 \, \text{(slechts 1 Level 2 tabel nodig)}.
    $$

- Aantal benodigde **Level 1 tables**:
  - Slechts 1 Level 1 tabel nodig omdat alle pagina's binnen dezelfde Level 1 range vallen.

3. **Stack segment:**

- **Startadres:** $0xF0000000$
- **Grootte:** $64 \, \text{KB}$.

Berekeningen:

- Aantal pagina's:

  $$
  \text{Aantal pagina's} = \frac{\text{Grootte}}{\text{Page size}} = \frac{64 \times 1024}{256} = 256.
  $$

- Aantal benodigde **Level 3 tables**:

  $$
  \frac{256}{64} = 4 \, \text{(afronden naar boven)}.
  $$

- Aantal benodigde **Level 2 tables**:

  - Elke Level 2 tabel bevat $256$ entries ($2^8$).
    $$
    \frac{4}{256} = 1 \, \text{(slechts 1 Level 2 tabel nodig)}.
    $$

- Aantal benodigde **Level 1 tables**:
  - Slechts 1 Level 1 tabel nodig omdat alle pagina's binnen dezelfde Level 1 range vallen.

Controle op samenvallende tables:

- **Level 3 tables:**
  Elke Level 3 tabel "beslaat" $64 \times 256 = 16 \, \text{KB} = 0x4000 \, \text{(hex)}$. Geen overlap tussen segmenten.

- **Level 2 tables:**
  Elke Level 2 tabel "beslaat" $256 \times 64 \times 256 = 16 \, \text{MB} = 0x1000000 \, \text{(hex)}$. Geen overlap.

- **Level 1 tables:**
  Elke Level 1 tabel "beslaat" $1024 \times 256 \times 256 = 1 \, \text{GB} = 0x40000000 \, \text{(hex)}$. Alle segmenten vallen binnen dezelfde Level 1 tabel.

Totale ruimte voor page tables:

Per tabel:

- Level 3 tables:
  $$
  45 \times 64 \times 4 = 11520 \, \text{bytes.}
  $$
- Level 2 tables:
  $$
  3 \times 256 \times 4 = 3072 \, \text{bytes.}
  $$
- Level 1 tables:
  $$
  1 \times 1024 \times 4 = 4096 \, \text{bytes.}
  $$

Totale ruimte:

$$
\text{Totale ruimte} = 11520 + 3072 + 4096 = 18688 \, \text{bytes.}
$$

**Antwoord:**

De page tables nemen in totaal **18688 bytes (18.25 KB)** in beslag.

### 2 Bepaal het aantal levels in een multilevel paging systeem

Stel dat een machine virtuele adressen heeft bestaande uit 36 bits en dat de pages 8K groot
zijn. Een enkele page entry is 8 bytes lang.

1. Uit hoeveel paginas bestaat de virtuele adresruimte?
   De virtuele adresruimte wordt bepaald door de totale hoeveelheid virtuele adressen en de grootte van een enkele pagina. Laten we dit stap voor stap berekenen:

Gegeven:

- **Virtueel adres**: 36 bits
- **Paginagrootte**: 8K (8 kilobyte = $2^{13}$ bytes)

1. **Virtuele adresruimte**:
   De virtuele adresruimte is de totale hoeveelheid adressen die met 36 bits kan worden weergegeven:

   $$
   2^{36} \text{ bytes (virtuele adresruimte)}
   $$

2. **Grootte van een pagina**:
   De grootte van een pagina is:

   $$
   2^{13} \text{ bytes (8K)}
   $$

3. **Aantal pagina's**:
   Het aantal pagina's in de virtuele adresruimte wordt berekend door de virtuele adresruimte te delen door de grootte van een pagina:
   $$
   \text{Aantal pagina's} = \frac{2^{36}}{2^{13}} = 2^{36 - 13} = 2^{23}
   $$

Conclusie:
De virtuele adresruimte bestaat uit $2^{23} = 8.388.608$ pagina's.

2. Stel dat een gemiddeld proces 8 Gbyte groot is. Hoeveel levels zijn er dan het meest geschikt indien we met een multilevel page table werken (bekijk 1 tot 3 levels)? Weeg de voor- en nadelen tegen elkaar af. Voor het systeem met 2 levels kies je de omvang van een level 2 page table zodanig dat deze precies past in een enkele page. Voor drie levels neem je een min of meer gelijke opdeling voor elk van de velden.

Bij het ontwerpen van een multilevel-pagetabel voor een virtueel geheugensysteem moeten we rekening houden met de omvang van de processen, de paginagrootte, en hoe efficiënt geheugen en opslag worden gebruikt. Laten we de berekeningen en overwegingen per niveau (1 tot 3 levels) bekijken.

**Gegeven:**

- Virtueel adres: 36 bits
- Paginagrootte: 8K ($2^{13}$ bytes)
- Gemiddeld procesgrootte: 8 GB ($2^{33}$ bytes)
- Page table entry (PTE): 8 bytes
- Multilevel pagetabel moet efficiënt gebruik maken van geheugen.

**Eén-level pagetable**

1. **Aantal pagina's voor een proces**:
   Een proces van 8 GB ($2^{33}$ bytes) bestaat uit:

   $$
   \text{Aantal pagina's} = \frac{2^{33}}{2^{13}} = 2^{20} \, \text{pagina's (1.048.576)}
   $$

2. **Grootte van de pagetable**:
   Elke pagina heeft een entry van 8 bytes. De totale grootte van een enkele pagetable is:

   $$
   \text{Grootte pagetable} = 2^{20} \times 8 = 2^{23} \, \text{bytes (8 MB)}.
   $$

3. **Overweging**:
   - **Voordelen**: Eenvoudig ontwerp, snelle toegang tot de fysieke adressen.
   - **Nadelen**: Pagetabel is groot en moet in zijn geheel in het geheugen passen. Dit kan leiden tot verspilling van geheugen als de pagetable grotendeels leeg is.

**Twee-level pagetable**

Bij een twee-level pagetable verdelen we het virtuele adres in drie delen:

- **Hoogste bits**: Indexeren de eerste level pagetable (L1).
- **Middelste bits**: Indexeren de tweede level pagetable (L2).
- **Laagste bits**: Offset binnen een pagina ($13$ bits voor $2^{13}$).

1. **Hoeveel bits voor elk niveau?**
   De L2-pagetabel moet precies in een enkele pagina passen. Een pagina is $2^{13}$ bytes groot, en elke entry is 8 bytes. Het aantal entries per L2-pagetabel is:

   $$
   \text{Aantal entries per L2-pagetabel} = \frac{2^{13}}{8} = 2^{10} \, \text{entries}.
   $$

   Om deze entries te adresseren zijn $10$ bits nodig.

   Dit betekent dat de adresbits als volgt worden verdeeld:

   - **13 bits**: Offset binnen een pagina.
   - **10 bits**: Voor L2-index.
   - **Overige $36 - 13 - 10 = 13$ bits**: Voor L1-index.

2. **Aantal benodigde pagetabellen**:
   Voor een proces van $2^{33}$ bytes ($2^{20}$ pagina's) zijn:

   - $2^{13}$ L2-pagetabellen nodig ($\frac{2^{20}}{2^{10}} = 2^{10}$).
   - Eén enkele L1-pagetabel, met $2^{13}$ entries ($13$ bits).

3. **Grootte van de pagetabellen**:

   - L1-pagetabel: $2^{13} \times 8 = 2^{16} = 64 \, \text{KB}$.
   - Alle L2-pagetabellen samen: $2^{10} \times 2^{13} = 2^{23} = 8 \, \text{MB}$.

4. **Overweging**:
   - **Voordelen**: Kleinere L1-pagetabel in het geheugen. Niet alle L2-pagetabellen hoeven geladen te worden, wat geheugen bespaart.
   - **Nadelen**: Complexere geheugenlookups (twee niveaus).

**Drie-level pagetable**

Bij een drie-level pagetable verdelen we het virtuele adres als volgt:

- **Hoogste bits**: Indexeren de L1-pagetabel.
- **Middelste bits**: Indexeren de L2-pagetabel.
- **Laagste bits**: Indexeren de L3-pagetabel.

We streven naar een evenwichtige verdeling van de bits over de niveaus, exclusief de offset ($13$ bits). Er blijven $36 - 13 = 23$ bits over om te verdelen.

1. **Verdeling van bits:**
   Bij een gelijke opdeling krijgen elk van de drie niveaus ongeveer:

   $$
   \frac{23}{3} \approx 7 \, \text{bits per niveau}.
   $$

   Dit betekent:

   - **7 bits voor L1**: $2^{7} = 128$ entries in de L1-pagetabel.
   - **7 bits voor L2**: $2^{7} = 128$ entries in elke L2-pagetabel.
   - **9 bits voor L3**: $2^{9} = 512$ entries in elke L3-pagetabel.

2. **Aantal pagetabellen**:
   Voor een proces van $2^{33}$ bytes ($2^{20}$ pagina's):

   - L1-pagetabel: 1 tabel ($2^{7}$ entries).
   - L2-pagetabellen: $2^{7}$ tabellen ($128$ tabellen).
   - L3-pagetabellen: $2^{7 + 9 - 10} = 512$ tabellen.

3. **Grootte van de pagetabellen**:

   - L1-pagetabel: $128 \times 8 = 1 \, \text{KB}$.
   - Alle L2-pagetabellen: $128 \times 1 \, \text{KB} = 128 \, \text{KB}$.
   - Alle L3-pagetabellen: $512 \times 4 \, \text{KB} = 2 \, \text{MB}$.

4. **Overweging**:
   - **Voordelen**: Geheugenbesparing, omdat alleen noodzakelijke pagetabellen in gebruik worden genomen.
   - **Nadelen**: Meerdere geheugentoegangen per adres, wat de snelheid beïnvloedt.

**Vergelijking**

| Niveau | Grootte pagetabellen | Geheugenbesparing | Toegangssnelheid | Geschiktheid |
| | -- | -- | - | |
| 1 | 8 MB | Laag | Hoog | Eenvoudig, maar inefficiënt voor grote processen. |
| 2 | 64 KB + 8 MB | Redelijk | Matig | Goede balans tussen complexiteit en geheugenverbruik. |
| 3 | 1 KB + 128 KB + 2 MB | Hoog | Laag | Efficiënt qua geheugen, maar trager door meerdere levels. |

**Conclusie**

Een **twee-level pagetable** biedt de beste balans tussen snelheid en geheugenbesparing, vooral voor een gemiddeld proces van 8 GB. Het systeem met drie levels is geschikter bij zeer grote processen of wanneer geheugen een kritische factor is.

### 3 Tel het aantal table misses

Beschouw volgend stukje code. Stel dat de binaire code op ´e´en page past en dat de stack
eveneens op een enkele page past. Je mag er bovendien van uit gaan dat bij het aanroepen
van de functie, de stack en code page reeds in de TLB cache zitten. Veronderstel verder dat
een integer 4 bytes lang is en dat een page 4096 bytes bevat.

```c
int a[1024][1024], b[1024][1024], c[1024][1024];
multiply() {
    unsigned i,j,k;
        for(i=0; i< 1024; i++){
            for(j=0; j< 1024; j++){
                for(k=0; k< 1024; k++){
                    c[i][j]+=a[i][k]*b[k][j];
                }
            }
        }
}
```

Gegeven dat de TLB cache slechts 8 entries bevat en dat hij een LRU replacement policy
gebruikt, wat is dan het aantal TLB misses bij de uitvoering van deze code?

Laten we de oplossing stap voor stap analyseren en controleren.

Probleemstelling
We analyseren het aantal **TLB misses** bij de uitvoering van de matrixvermenigvuldiging in de gegeven code. De TLB cache heeft slechts 8 entries met een **Least Recently Used (LRU)** vervangingsbeleid.

Belangrijke gegevens:

- Elke matrix ($a$, $b$, $c$) is $1024 \times 1024$.
- Elke pagina is $4096$ bytes groot.
- Een integer is $4$ bytes.
- Een pagina bevat $4096 / 4 = 1024$ elementen (1 rij van een matrix).
- Elke matrix beslaat $1024$ pagina's (één pagina per rij).

TLB-entries
De TLB bevat 8 entries:

- 2 entries worden permanent gebruikt voor **code** en **stack**.
- 6 entries blijven over voor de arrays $a$, $b$, en $c$.

---

### Gedetailleerde analyse

De code bevat drie geneste for-loops:

```c
for(i = 0; i < 1024; i++) {
    for(j = 0; j < 1024; j++) {
        for(k = 0; k < 1024; k++) {
            c[i][j] += a[i][k] * b[k][j];
        }
    }
}
```

1. **Vaste waarde van $i$**:

   - Binnen de **$j$-loop** wordt element $c[i][j]$ bewerkt.
     - $c[i][j]$ bevindt zich op dezelfde pagina zolang $j$ binnen de eerste 1024 elementen van een rij blijft.
     - Resultaat: **1 TLB miss voor $c[i][j]$** bij de eerste toegang per rij van $c[i][j]$.
   - Voor array $a[i][k]$:
     - $a[i][k]$ blijft binnen dezelfde pagina zolang $k$ binnen de eerste 1024 elementen van een rij blijft.
     - Resultaat: **1 TLB miss voor $a[i][k]$** bij de eerste toegang per rij van $a[i][k]$.
   - Voor array $b[k][j]$:
     - Hier wordt $b[k][j]$ per iteratie door de $k$-loop een **nieuwe rij** van $b$ aangesproken, wat steeds een nieuwe pagina vereist.
     - Resultaat: **1 TLB miss per $k$** (dus $1024$ misses per iteratie van $j$).

   **Samenvatting per $j$-iteratie:**

   - $1$ miss voor $a[i][k]$.
   - $1$ miss voor $c[i][j]$.
   - $1024$ misses voor $b[k][j]$.
   - **Totaal: $2 + 1024$ TLB misses per $j$-iteratie.**

2. **Iteratie over $j$:**

   - Er zijn $1024$ $j$-iteraties per $i$.
   - Per $j$-iteratie: $2 + 1024$ misses.
   - **Totaal per $i$: $1024 \times (2 + 1024) = 1049600$ TLB misses.**

3. **Iteratie over $i$:**
   - Er zijn $1024$ $i$-iteraties.
   - Per $i$: $1049600$ misses.
   - **Totaal: $1024 \times 1049600 = 1073741824$ TLB misses.**

---

Conclusie
De oplossing lijkt correct. Het totale aantal TLB misses bij de uitvoering van de code is:

$$
\boxed{1073741824}
$$
