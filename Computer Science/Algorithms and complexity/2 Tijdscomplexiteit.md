# 2.1 Deterministisch polynomiale tijd (PTIME)
**Polynomiale tijd (PTIME)**: de tijd die het kost om een probleem op te lossen, begrensd is door een polynomiale functie van de grootte van de invoer. De uitvoeringstijd van het algoritme kan worden uitgedrukt als $O(n^k)$, waarbij n de grootte van de invoer is en K een bepaalde constante.

**Exhaustieve enumeratie**: een probleemoplossingstechniek waarbij alle mogelijke oplossingen systematisch worden gegenereerd en onderzocht om de gewenste oplossing te vinden.

**Polynomiale tijdcomplexiteit**: als de tijd die het kost om het probleem op te lossen, kan worden uitgedrukt als een polynomiale functie van de grootte van de invoer.

Alle deterministische berekeningsmodellen zijn polynomiaal equivalent (d.w.z. dat deze modellen kunnen in elkaar worden getransformeerd in polynomiale tijd)

**Deterministische tijdscomplexiteitsklasse (DTIME(t(n)))**:$\text{DTIME}(t(n)) = \{L | \text{de taal } L \text{ wordt beslist door een } O(t(n)) \text{-tijd deterministische Turing machine met één tape} \}$
### Voorbeeld:
Veronderstel dat je computer 100 miljoen stappen doet per seconde.
De onderstaande tabel toont de CPU tijd voor verschillende functies t ∶ N → N.
![[Screenshot 2024-06-23 at 20.52.00.png]]

PTIME = de klasse van alle talen die beslist kunnen worden door een deterministische TM met één tape, en dit in polynomiale tijd
$PTIME = \underset{k} \cup DTIME (n^k)$

*Representatie van een object* x als woord: $\langle x \rangle$ (object kan een graaf, formule of een getal zijn)

Voor een geheel getal n nemen we meestal $\langle n \rangle$ als de binaire representatie van dat getal

**Ongerichte graaf**: Een graaf waarbij de randen geen richting hebben. Als er een rand is die een knooppunt met een ander verbindt, betekent dit dat de twee knooppunten verbonden zijn, zonder enige richting te impliceren.

**Gerichte graaf**: In tegenstelling tot een ongerichte graaf, hebben de randen in een gerichte graaf een richting. Dit betekent dat als er een rand is van knooppunt A naar knooppunt B, het betekent dat A verbonden is met B, maar niet noodzakelijk vice versa.

$PATH = \{ \langle G,s,t \rangle | G \text { is een gerichte graaf met een pad van vertex s naar t} \}$

*PTIME algoritme*: Breadth-first search.
M = Op input $\langle G,s,t  \rangle$ met G een gerichte graaf met beginknoop s en eindknoop t:
1. Markeer de startknoop s (**eenmaal**)
2. Herhaal tot geen nieuwe markeringen op knopen gemaakt kunnen worden (**m-keer**)
3. Doorloop de bogen in G. Als (aub) een boog is met gemarkeerde knoop a en niet gemarkeerde knoop b, dan markeer b
4. Als de eindknoop t gemarkeerd is dan aanvaard de input zonet verwerp (**eenmaal**)

- Stappen 1 en 4 zijn in polynomiale tijd.
- Stap 3 vraagt om de input te scannen en te testen welke knopen gemarkeerd zijn, dit kan ook in polynomiale tijd
- Stap 4 herhalen we m keer (m aantal knopen)