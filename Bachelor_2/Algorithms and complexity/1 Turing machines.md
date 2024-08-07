# 1.1 Deterministische Turing machines
**Turing machine**: krachtige abstracte modellen voor berekeningen, die bestaan uit een eindige controle, een oneindige tape en een lees/schrijfkop. Ze bieden een formele manier om de berekenbaarheid van problemen te onderzoeken.

Alle bekende algoritmen kunnen worden geïmplementeerd door een Turing machine.

Alle programma’s van een Turing machine kunnen worden geïmplementeerd in een programmeertaal dat uitgevoerd kan worden op een computer.

Elke andere bestaande formalisering kan herleid worden tot die van een Turing machine.

**Alfabet Σ**: een eindige verzameling van symbolen

**Woord w over Σ**: een eindige reeks van symbolen in Σ

**Σ∗**: De verzameling van alle woorden over Σ

**Een taal L over Σ**: een verzameling van woorden over Σ.

Deterministische Turing machine ($Q$, $Σ$, $Γ$, $δ$, $q_0$, $q_{accept}$, $q_{reject}$)
- $Q$ een eindige verzameling van toestanden (states)
- $Σ$ het input alfabet
- $Γ$ het tape alfabet
- $q_0 ∈ Q$ de begintoestand (initial state)
- $q_{accept} ∈ Q$ de aanvaardingstoestand (accepting state)
- $q_{reject} ∈ Q$ de verwerpingstoestand (rejecting state) ($q_{accept} ≠ q_{reject}$)
- $δ$ een partiële functie (transitiefunctie)

het ⊢ symbool markeert de positie 0 (meest linkse positie) op de tape.

De uitvoering van de machine zorgt voor een (mogelijke) verandering in: 
- de huidige toestand van de machine;
- de inhoud van de tape; en
- de huidige positie van de lees/schrijfkop.

![[Screenshot 2024-06-21 at 09.52.08.png]]

De startconfiguratie op input w is altijd ⊢ q0w.
In de aanvaardingsconfiguratie de toestand is altijd $q_{accept}$.
In de verwerpingsconfiguratie de toestand is altijd $q_{reject}$.
De toestanden $q_{accept}$ en $q_{reject}$ zijn zogenaamde stoptoestanden (halting states). Wanneer de machine zich in een stoptoestand bevindt kunnen geen verdere configuraties worden bekomen.

# 1.2 Algoritmen en beslissers
**Algoritme**: Turing machine dewelke stopt op elke input.

**Beslisser**: Turing machine die op elke input stop (niet elke input wordt geaccepteerd maar kan ook afgewezen worden).

**Turing-beslisbaar**: taal die aanvaard wordt door een beslisser

![[Screenshot 2024-06-21 at 09.55.06.png]]

# 1.3 Tijdscomplexiteit
**Computationele complexiteit**: de studie van de middelen (zoals tijd en ruimte) die door algoritmes nodig zijn om computationele problemen op te lossen

Voor een TM met alfabet Σ:
- Stap van M: Het uitvoeren van één instructie van de transitie functie(van de ene configuratie naar een andere).
- TimeM(w): het aantal stappen dat M uitvoert op input w ∈ Σ*

**“worst case” tijdscomplexiteit** van een TM M: is gedefinieerd als de functie tM:
$T_M(n) = \max \{ \text{time}_M(w) | w \in \Sigma * \text{ en } |w| = n \}$

In complexiteitstheorie zijn we zelden geïnteresseerd in de exacte tijdscomplexiteit (precies aantal stappen). Eerder, we zijn geïnteresseerd in hoe tijdscomplexiteit groeit wanneer input langer wordt. We kijken daarom naar tijdscomplexiteit wanneer de input lengte naar oneindig gaat.

# 1.4 Asymptotische analyse
**Big O (O-notatie)**: De notatie "$O(f(n))$" geeft de bovengrens aan van de groeisnelheid van een functie of algoritme. Het vertelt ons dat de functie of algoritme niet sneller zal groeien dan een bepaalde snelheid die wordt aangegeven door de functie "$f(n)$".

**Big Omega (Ω-notatie)**: De notatie "$Ω(f(n))$" geeft de ondergrens aan van de groeisnelheid van een functie of algoritme. Het vertelt ons dat de functie of algoritme niet langzamer zal groeien dan een bepaalde snelheid die wordt aangegeven door de functie "$f(n)$".

Een TM M loopt in tijd $O(t(n))$ als $tM(n)$ van orde $O(t(n))$ is.

# 1.5 Beslissingsproblemen
**Beslissingsprobleem** geassocieerd met een taal L: Gegeven een woord w ∈ Σ∗, beslis (ja/nee) of w ∈ L.

Een taal L wordt beslist door een TM M in tijd O(t(n)) als L = L(M) en tM (n) is van orde O(t(n)).

**Complexiteit** van een taal L: de complexiteit van het beslissingsprobleem geassocieerd met L.

Even beslissingsprobleem kan efficiënt worden opgelost als er een efficiënt algoritme bestaat dat het probleem beslist. 

Een TM berekent een functie f ∶ Σ∗ → Σ∗ als en slechts dan voor elk input woord w, f (w) de output is van de TM.

**Church-Turing-thesis**: thesis die zegt dat elke wiskundig berekenbare functie berekend kan worden door een Turingmachine, en omgekeerd, elke functie die door een Turingmachine berekend kan worden, kan wiskundig worden gedefinieerd.

# 1.6 Deterministische Turing machines met meerdere tapes

Een deterministische TM met k tapes wordt gegeven door: 

$(Q, Σ, Γ, δ, q0, q_{accept}, q_{reject})$:
- $Q$ een eindige verzameling van toestanden (states)
- $Σ$ het input alfabet
- $Γ$ het tape alfabet
- $q_0$ ∈ Q de begintoestand (initial state)
- $q_{accept} ∈ Q$ de aanvaardingstoestand (accepting state)
- $q_{reject} ∈ Q$ de verwerpingstoestand (rejecting state) ($q_{accept}$ ≠ $q_{reject}$)
- $δ$ een partiële functie (transitiefunctie) $\delta : Q \times \Gamma ^k \rightarrow Q \times \Gamma ^k\times \{ \leftarrow, \Box , \rightarrow \}^k$

De machine heeft k tapes, oneindig doorlopend naar rechts

De machine heeft één lees/schrijfkop per tape

Positie 0 wordt aangegeven door “⊢” symbool

Voorbeeld configuratie: ```#u1qv1#u2qv2#…#ukqvk```

Als een taal L beslist wordt door een k-tape TM M, dan wordt deze taal ook beslist door een TM S met 1 tape.

Informeel bewijs: **Simulatie multitape machine**
- De k tapes van M worden eerst op de (enige) tape van S gekopiëerd.
- Hier gebruiken we # om de inhoud van de verschillende tapes te onderscheiden (net zoals in de configuraties).
- Om de positie van de koppen aan te duiden gebruikt S nieuwe symbolen op de tape.
- Bijvoorbeeld, als kop staat over een symbool a, duiden we dit aan met ã. Maw, S heeft ã in zijn tape alfabet, voor elke a in het tape alfabet van M. Zie dit als virtuele tapes en koppen.

**Werking van simulatie multitape machine door single TM S:**
S = Op input $w = w_1…w_n$:
1. Simuleer de initiële configuratie van M op w:
	$\vdash \# \tilde{w}_1w_2 ... w_n \# \tilde {\sqcup}\# \tilde{\sqcup}...\# \tilde {\sqcup}\#$

2. S scant de tape om te kijken waar elke kop zich bevind, vervolgens maakt S een tweede scan van de tape en updatet de tape zoals beschreven door de transitiefunctie van M.
3. Als de virtuele kop naar rechts beweegt en op # staat, wil dit zeggen dat M een kop beweegt naar een positie die nog niet bezocht was en dus een ⊔ bevat. Dus S schrijdt een ⊔ en schuit alle inhoud erna 1 positie naar rechts op (right shifting).

![[Screenshot 2024-06-21 at 10.16.34.png]]

Als een taal L beslist wordt door een TM M met k tapes (k ≥ 2) in tijd O(t(n)), met t(n) ≥ n, dan wordt L beslist door een TM S met 1 tape in tijd O(t(n)2). Dit tijdscomplexiteit kan niet worden vermeden.

**Crossing sequence**: een sequentie van configuraties van een Turingmachine die wordt gebruikt om de interactie tussen de machine en een gegeven invoer te beschrijven

Ci(x) Voor een input woord x en positie i op de tape: de lijst van toestanden in Q waarin M zich bevindt als deze beweegt tussen positie i and i + 1 op input x.

![[Screenshot 2024-06-21 at 10.17.50.png]]

# 1.7 Niet-Deterministische Turing machines
Een niet-deterministische TM (NTM) wordt gegeven door:
$(Q, Σ, Γ, δ, q0, q_{accept}, q_{reject})$:
- $Q$ een eindige verzameling van toestanden (states)
- $Σ$ het input alfabet
- $Γ$ het tape alfabet
- $q0 ∈ Q$ de begintoestand (initial state)
- $q_{accept}$, $q_{reject}$ $∈ Q$ zijn de aanvaardings- en verwerpingstoestanden
- $δ$ is een relatie: $\delta :	\subseteq Q \times \Gamma\rightarrow Q \times \Gamma \times \{ \leftarrow, \Box , \rightarrow \}$  

Verschil tussen DTM en NTM:
- Een deterministische Turingmachine kiest altijd een specifieke overgang om te volgen.
- Een niet-deterministische Turingmachine kan bij elke stap een van de mogelijke overgangen kiezen, maar gaat vervolgens verder langs een enkel pad.
  
Een niet-deterministische TM M aanraadt een input woord w als:
Er een reeks van configuraties C1, C2, …, Ck bestaat zodat: 
1. C1 is de beginconfiguratie van M op input w
2. Ci leidt tot Ci+1
3. Ck is een aanvaardingsconfiguratie

Slechts één aanvaardingsreeks van configuraties nodig om een taal te beslissen

**Berekeningsboom**: grafische representatie die de mogelijke computationele paden van de TM voor een specifieke invoer illustreert

![[Screenshot 2024-06-21 at 10.22.41.png]]
  

Tijdscomplexiteit van een NTM M:
$\max \{ \text{time}_M(w) | w \in \Sigma^* \text{ en } |w| = n \}$

NTM kunnen even veel talen beslissen als en DTM maar het kan mogelijk op een efficiëntere manier. 

Stelling: Stel, t(n) is een functie zodat t(n) ≥ n. Dan, elke niet-deterministische TM N die loopt in tijd O(t(n)) is equivalent met een deterministische TM D die loopt in de tijd 2O(t(n))

**Breadth-First Search (BFS)**: algoritme dat wordt gebruikt voor het doorzoeken of traverseren van grafen of bomen. Het garandeert dat het kortste pad tussen het startknooppunt en elk ander bereikbaar knooppunt als eerste wordt gevonden.